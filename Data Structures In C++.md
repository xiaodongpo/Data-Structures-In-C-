# 一.概论
![alt text](image.png)
## 1.1基本术语
![alt text](image-1.png)
**数据元素**是数据的基本单位，通常作为一个整体进行考虑和处理。
一个数据元素可由若干**数据项**构成，数据项是构成数据元素的不可分割的最小单位。
**数据对象**是具有<u>相同性质</u>的数据元素的集合。
**数据结构**是相互之间存在一种或多种特定关系的数据元素的集合。
注：同一个数据对象里的数据元素，可以组成不同的数据结构。
![alt text](image-2.png)

---
## 1.2 数据结构的三要素
![alt text](<屏幕截图 2024-05-27 093802.png>)
1.  **逻辑结构**，定义一种数据结构；
2.  **物理结构（存储结构）**，如何用计算机实现这种数据结构，表现数据元素的逻辑关系。 
    - 顺序存储：把逻辑上相邻的元素存储在物理位置也相邻的存储单元中，元素之间的关系由存储单元的邻接关系来体现。
    - 链式存储：逻辑上相邻的元素在物理位置上可以不相邻，借助指示元素存储地址的指针来表示元素之间的逻辑关系。
    - 索引存储：在存储元素信息的同时，还建立附加的索引表，索引表中的每项称为索引项，索引项的一般形式是（关键字，地址）。
    - 散列存储：根据元素的关键字直接计算出该元素的存储地址，又称哈希（Hash）存储。

注：
- 若采用顺序存储，则各个数据元素在物理上必须是连续的;若采用非顺序存储，则各个数据元素在物理上可以是离散的。
- 数据的存储结构会影响存储空间分配的方便程度。
- 数据的存储结构会影响对数据运算的速度
3. **数据的运算**
    - 数据上的运算包括运算的定义和实现。
    - 运算的定义是针对逻辑结构指出运算的功能。
    - 运算的实现是针对存储结构的，指出运算的具体操作步骤。
---
## 1.3 算法的基本概念
![alt text](image-3.png)
***程序 = 数据结构+算法***
- 数据结构：如何用数据正确地描述现实世界的问题，并存入计算机。
- 算法：是对特定问题求解步骤的一种描述，它是指令的有限序列，其中的每条指令表示一个或多个操作。（如何高效地处理这些数据，以解决实际问题）
- 算法的特性： 
    - 有穷性：一个算法必须总在执行有穷步之后结束，且每一步都可在有穷时间内完成。
    - 确定性：算法中每条指令必须有确定的含义，对于相同的输入只能得到相同的输出。
    - 可行性：算法中描述的操作都可以通过已经实现的基本运算执行有限次来实现。
    - 输入：一个算法有零个或多个输入，这些输入取自于某个特定的对象的集合。
    -输出：一个算法有一个多个输出，这些输出是与输入有着某种特定关系的量。
- 好的算法达到的目标：
    - 正确性：算法应能够正确的求解问题。
    - 可读性：算法应具有良好的可读性，以帮助人们理解。
    - 健壮性：输入非法数据时，算法能适当地做出反应或进行处理，而不会产生莫名奇妙地输出结果。
    - 效率与低存储量需求：花的时间少即：时间复杂度低。不费内存即：空间复杂度低。
---
## 1.4 时间复杂度
![alt text](image-4.png)
- 顺序执行的代码只会影响常数项，可以忽略。
- 只需挑循环中的一个基本操作分析它的执行次数与 n 的关系即可。
- 如果有多层嵌套循环只需关注最深层循环循环了几次。
![alt text](image-5.png)
---
## 1.5 空间复杂度
![alt text](image-6.png)
- 指算法消耗的存储空间(即算法除本身所需存储外的辅助空间)
- 算法的空间复杂度S(n)定义为该算法所耗费的存储空间，它是问题规模n的函数。
记为S(n)=O(g(n))
![alt text](image-7.png)
---
# 二.线性表
## 2.1线性表的定义和基本操作
**线性表**是具有**相同数据类型**的n(n>0)个数据元素的**有限序列**。
(其中n为表长，当n=0时线性表是一个空表。若用L命名线性表，则其一般表示为)
L=(a<sub>1</sub>,a<sub>2</sub>,...,a<sub>i</sub>,a<sub>n</sub>,)
1. 特点：
    - 存在惟一的第一个元素。
    - 存在惟一的最后一个元素。
    - 除第一个元素之外，每个元素均只有一个直接前驱。
    - 除最后一个元素之外，每个元素均只有一个直接后继
2. 几个概念:
   - a<sub>i</sub>是线性表中的“第i个”元素线性表中的位序。a<sub>1</sub>是表头元素;a<sub>n</sub>是表尾元素。
    - 除第一个元素外，每个元素有且仅有一个直接前驱:除最后一个元素外，每个元素有且仅有一个直接后继。
3. 存储结构：
    - 顺序存储结构：顺序表
    - 链式存储结构：链表
4. 基本操作
    - InitList(&L)：初始化表。构造一个空的线性表L，分配内存空间。
    - DestroyList(&L)： 销毁操作。销毁线性表，并释放线性表L所占用的内存空间。
    - ListInsert(&L;i,e)：插入操作。在表L中的第i个位置上插入指定元素e。 
    - ListDelete(&L,i,&e)：删除操作。删除表L中第i个位置的元素，并用e返回删除元素的值。
    - LocateElem(L,e)：按值查找操作。在表L中查找具有给定关键字值的元素。
    - GetElem(L,i): 按位查找操作。获取表L中第i个位置的元素的值。
    - Length(L)：求表长。返回线性表L的长度，即L中数据元素的个数。
    - PrintList(L)：输出操作。按前后顺序输出线性表L的所有元素值。
    - Empty(L)：判空操作。若L为空表，则返回true，否则返回false。
![alt text](image-8.png)
---
## 2.2顺序表的定义和基本操作
![alt text](顺序表.png)
### 顺序表的静态分配
```c++
#define MaxSize 10          //定义表的最大长度
typedef struct {
    int data[MaxSize];      //用静态的"数组"存放数据元素
    int length;             //顺序表的当前长度
} SqList;                    //顺序表的类型定义（静态分配方式）

void InitList(SqList &L) {
    for (int i = 0; i < MaxSize; i++) {
        L.data[i] = 0;        //将所有数据元素设置为默认初始值
    }
    L.length = 0;
}
```
### 顺序表的动态分配
```c++
struct SeqList {
    int *data;    // 指示动态分配数组的指针
    int MaxSize;  // 顺序表的最大容量
    int length;   // 顺序表的当前长度
};

void InitList(SeqList &L) {                 // 初始化
    // 用new 函数申请一片连续的存储空间
    L.data = new int[InitSize];
    L.length = 0;
    L.MaxSize = InitSize;
}

void IncreaseSize(SeqList &L, int len) {  // 增加动态数组的长度
    int *p = L.data;
    L.data = new int[L.MaxSize + len];
    for (int i = 0; i < L.length; i++) {
        L.data[i] = p[i];      // 将数据复制到新区域
    }
    L.MaxSize = L.MaxSize + len; // 顺序表最大长度增加len
    delete[] p;                 // 释放原来的内存空间
}

int main() {
    SeqList L;        // 声明一个顺序表
    InitList(L);      // 初始化顺序表
    IncreaseSize(L, 5); // 增加顺序表的长度
    return 0;
}
```
### 顺序表的插入操作
ListInsert(&L,i,e)：插入操作。在表L中的第i个位置上插入指定元素e。
```c++
#define MaxSize 10 //定义最大长度

struct SqList {
    int data[MaxSize];  //用静态的数组存放数据
    int length;         //顺序表的当前长度
};                //顺序表的类型定义

bool ListInsert(SqList &L, int i, int e) {
    if (i < 1 || i > L.length + 1)    //判断i的范围是否有效
        return false;
    if (L.length >= MaxSize) //当前存储空间已满，不能插入
        return false;

    for (int j = L.length; j >= i; j--) {    //将第i个元素及其之后的元素后移
        L.data[j] = L.data[j - 1];
    }
    L.data[i - 1] = e;  //在位置i处放入e
    L.length++;      //长度加1
    return true;
}

void InitList(SqList &L) {
    L.length = 0;
}
```
- 时间复杂度
最好情况：新元素插入到表尾，不需要移动元素（i = n+1,循环0次),最好时间复杂度=O(1)
最坏情况：新元素的插入到表头，需要将原有的n个元素全部向后移动（i=1，循环n次），最坏时间复杂度=O(n)
平均情况：假设新元素插入到任何一个位置的概率相同，即i=1,2,3,...,length+1的概率都是$p={1\over n+1}$。
i=1，循环n次；i=2，循环n-1次；...;i=n+1，循环0次。平均循环次数 =np+(n-1)p+...+1*p=${n(n+1)\over 2}{1\over n+1}$=$\frac n2$ ->平均时间复杂度 = O(n)
---
### 顺序表的删除操作
```c++
// 删除顺序表i位置的数据并存入e
bool ListDelete(SqList &L, int i, int &e) {
    if (i < 1 || i > L.length) // 判断i的范围是否有效
        return false;
    e = L.data[i-1]; // 将被删除的元素赋值给e 
    for (int j = i; j < L.length; j++) //将第i个位置后的元素前移 
        L.data[j-1] = L.data[j];
    L.length--;
    return true; 
}

int main() {
    SqList L;
    InitList(L);
    int e = -1;
    if (ListDelete(L, 3, e))
        cout << "已删除第3个元素，删除元素值为" << e << endl;
    else
        cout << "位序i不合法，删除失败" << endl; 
    return 0; 
}
```
- 时间复杂度
最好情况：删除表尾元素，不需要移动其它元素（i=n,循环0次),最好时间复杂度=O(1)
最坏情况：删除表头元素，需要将后续的n-1个元素全部向前移动（i=1，循环n-1次），最坏时间复杂度=O(n)
平均情况：假设删除任何一个元素的概率相同，即i=1,2,3,...,length的概率都是$p={1\over n}$。
i=1，循环n-1次；i=2，循环n-2次；...;i=n，循环0次。平均循环次数 =(n-1)p+(n-2)p...+1*p=${n(n-1)\over 2}{1\over n}$=$n-1\over 2$ ->平均时间复杂度 = O(n)

**代码中要注意位序i和数组下标的区别**
### 顺序表的查找
- 按位查找
GetElem(L,):按位查找操作。获取表L中第i个位置的元素的值
```c++
ElemType GetElem(SqList L, int i) {
	return L.data[i-1];
}
/*时间复杂度：0(1)
由于顺序表的各个数据元素在内存中连续存放。因此可以根据起始地址和数据元素大小立即找到第i个元素--“随机存取”特性*/
```
- 按值查找
LocateElem(L,e): 按值查找操作。在表L中查找具有给定关键字值的元素
```c++
//在顺序表L中查找第一个元素值等于e的元素，并返回其位序
int LocateElem(SqList L, ElemType e){
    for(int i=0; i<L.lengthl i++)
        if(L.data[i] == e)  
            return i+1;     //数组下标为i的元素值等于e，返回其位序i+1
    return 0;               //推出循环，说明查找失败
}
```
基本数据类型：int、char、double、float等可以直接用运算符“==”比较。
结构类型的比较：定义一个函数
时间复杂度：
最好情况：目标元素在表头，O(1)
最坏情况：目标元素在表尾，O(1)
平均情况：目标元素出现在任何一个位置的概率相同，为${\frac 1n}$。目标元素在第n位，循环n次。平均循环次数=1${\frac 1n}$+2${\frac 1n}$...+n*${\frac 1n}$=${n(n+1)\over 2}{1\over n}$=$n+1\over 2$ 

---
## 2.3链表的定义和基本操作
### 单链表
- 单链表：用链式存储实现了线性结构。一个结点存储一个数据元素，各结点间的前后关系用一个指针表示。
- 优点：不要求大片连续空间，改变容量方便。
  缺点：不可随机存取，要耗费一定空间存放指针。
- 实现方式：
    - 带头结点，写代码更方便。头结点不存储数据，头结点指向的下一个结点才存放实际数据。
    - 不带头结点，对第一个数据结点与后续数据结点的处理需要用不同的代码逻辑;对空表和非空表的处理需要用不同的代码逻辑;头指针指向的结点用于存放实际数据;
### 2.3.1定义一个单链表
```c++
typedef struct LNode
{                      //定义单链表结点类型
    ElemType data;     //数据域
    struct LNode *next;//指针域
}LNode, *LinkList;
//typedef <数据类型> <别名>
```
上述代码其实等价于
```c++
struct LNode{
    ElemType data;
    struct LNode *next;
};
typedef struct LNode LNode;
typedef struct LNode *LinkList;
```
强调这是一个单链表--使用 LinkList
强调这是一个结点--使用 LNode*
(实际上 LinkList只是LNode * 的别名)
### 不带头节点的单链表
```c++ 
//初始化一个空的单链表
bool InitList(LinkList &L){
    L = NULL; //空表，暂时还没有任何结点
    return true;
}
 
void test(){
    LinkList L;  //声明一个指向单链表的头指针
    //初始化一个空表
    InitList(L);
    ...
}
 
//判断单链表是否为空
bool Empty(LinkList L){
    return (L==NULL)
}
```
### 带头节点的单链表
```c++ 
// 初始化一个单链表（带头结点）
bool InitList(LinkList &L) {
    L = new LNode; // 头指针指向的结点——分配一个头结点（不存储数据）
    if (L == NULL)          //内存不足，分配失败
        return false;
    L -> next = NULL;       //头结点之后暂时还没有结点
    return true;
}

void test() {
    LinkList L; //声明一个指向单链表的指针： 头指针
    //初始化一个空表
    InitList(L);
    //...
}

//判断单链表是否为空（带头结点）
bool Empty(LinkList L) {
    if (L->next == NULL)
        return true;
    else
        return false;
}
```
### 2.3.2单链表的插入删除
![alt text](image-9.png)
#### 按位序插入（带头结点）
Listlnsert(&Li,e): 插入操作。在表L中的第i个位置上插入指定元素e
找到第i-1个结点(前驱结点)，将新结点插入其后；其中头结点可以看作第0个结点，故i=1时也适用。
平均时间复杂度:O(n)
```c++
// 在第i个位置插入元素e（带头结点）
bool ListInsert(LinkList &L, int i, ElemType e) {
    // 判断i的合法性， i是位序号(从1开始)
    if (i < 1)
        return false;

    LNode *p;       // 指针p指向当前扫描到的结点
    int j = 0;      // 当前p指向的是第几个结点
    p = L;          // p和L指向头结点，头结点是第0个结点（不存数据）

    // 循环找到第i-1个结点
    while (p != NULL && j < i - 1) {     // 如果i>lengh, 经此循环p最后会等于NULL
        p = p->next;                     // p指向下一个结点
        j++;
    }

    if (p == NULL)                      
        return false;

    // 在第i-1个结点后插入新结点
    LNode *s = new LNode;               // 申请一个结点
    s->data = e;
    s->next = p->next;
    p->next = s;                        // 将结点s连到p后，后两步千万不能颠倒

    return true;
}
```
平均时间复杂度：O(n)
#### 按位序插入（不带头结点）
不存在“第0个”节点，当i=1时，插入、删除第一个元素时，需要更改头指针L。写代码不方便，推荐用带头节点
```c++
bool ListInsert(LinkList &L, int i, ElemType e) {
    if (i < 1)
        return false;

    // 插入到第1个位置时的操作有所不同！
    if (i == 1) {
        LNode *s = new LNode;
        s->data = e;
        s->next = L;
        L = s;          // 头指针指向新结点
        return true;
    }

    // i>1的情况与带头结点一样！唯一区别是j的初始值为1
    LNode *p;       // 指针p指向当前扫描到的结点
    int j = 1;      // 当前p指向的是第几个结点
    p = L;          // L指向头结点，头结点是第0个结点（不存数据）

    // 循环找到第i-1个结点
    while (p != NULL && j < i - 1) {     // 如果i>lengh, p最后会等于NULL
        p = p->next;                     // p指向下一个结点
        j++;
    }

    if (p == NULL)                      // i值不合法
        return false;

    // 在第i-1个结点后插入新结点
    LNode *s = new LNode;               // 申请一个结点
    s->data = e;
    s->next = p->next;
    p->next = s;
    return true;
}
```
#### 指定结点的后插操作
InsertNextNode(LNode *p, ElemType e)；
给定一个结点p，在其之后插入元素e; 根据单链表的链接指针只能往后查找，故给定一个结点p，那么p之后的结点我们都可知，但是p结点之前的结点无法得知
```c++
bool InsertNextNode(LNode *p, ElemType e)
{
    if(p == NULL){
        return false;
    }

    LNode *s = new LNode();
    //某些情况下分配失败，比如内存不足
    if(s == NULL)
        return false;
    s->data = e;          //用结点s保存数据元素e 
    s->next = p->next;
    p->next = s;          //将结点s连到p之后

    return true;
}                         //平均时间复杂度 = O(1)

```
#### 指定结点的前插操作
设待插入结点是s，将s插入到p的前面。我们仍然可以将s插入到*p的后面。然后将p->data与s->data交换，这样既能满足了逻辑关系，又能是的时间复杂度为O(1)
```c++
bool InsertPriorNode(LNode *p, LNode *s){
    if(p==NULL|| s ==NULL)
        return false;
    s->next = p->next;
    p->next = s;       //新结点s连到p之后
    ElemType temp = p->data;//保存节点p中数据
    p->data = s->data; 
    s->data = temp;       
    return true;
}
```
#### 按位序删除（带头结点）
按位序删除节点
ListDelete(&L, i, &e): 删除操作，删除表L中第i个位置的元素，并用e返回删除元素的值;头结点视为“第0个”结点；
思路：找到第i-1个结点，将其指针指向第i+1个结点，并释放第i个结点
平均时间复杂度：O(n)
```c++
bool ListDelete(LinkList &L, int i, ElenType &e){
    if(i<1) return false;
 
    LNode *p;       //指针p指向当前扫描到的结点 
    int j=0;        //当前p指向的是第几个结点
    p = L;          //L指向头结点，头结点是第0个结点（不存数据）
 
    //循环找到第i-1个结点
    while(p!=NULL && j<i-1){     //如果i>lengh, p最后会等于NULL
        p = p->next;             //p指向下一个结点
        j++;
    }
 
    if(p==NULL) 
        return false;
    if(p->next == NULL) //第i-1个结点之后已无其他结点
        return false;
 
    LNode *q = p->next;         //令q指向被删除的结点
    e = q->data;                //用e返回被删除元素的值
    p->next = q->next;          //将*q结点从链中“断开”
    delete q                    //释放结点的存储空间
 
    return true;
}
```
#### 指定结点的删除
```c++
bool DeleteNode(LNode *p){
    if(p==NULL)
        return false;
    
    LNode *q = p->next;      //令q指向*p的后继结点
    p->data = p->next->data; //让p和后继结点交换数据域
    p->next = q->next;       //将*q结点从链中“断开”
    delete q;
    return true;
} //时间复杂度 = O(1)
//如果p是最后一个结点，只能从表头开始以此寻找p的前驱，时间复杂度为O(n)
```
单链表的局限性：无法逆向检索，有时候不太方便
### 2.3.3单链表的查找
单链表不具备“随机访问”特性，只能依次扫描
#### 单链表的按位查找
GetElem(L, i): 按位查找操作，获取表L中第i个位置的元素的值;
平均时间复杂度O(n)
```c++
LNode * GetElem(LinkList L, int i){
    if(i<0) return NULL;
    
    LNode *p;               //指针p指向当前扫描到的结点
    int j=0;                //当前p指向的是第几个结点
    p = L;                  //L指向头结点,头结点是第0个结点(不存数据)
    while(p!=NULL && j<i){  //循环找到第i个结点
        p = p->next;
        j++;
    }
 
    return p;               //返回p指针指向的值
}
```
#### 单链表的按值查找
LocateElem(L, e):按值查找操作，在表L中查找具有给定关键字值的元素;
平均时间复杂度:O(n)
```c++
LNode * LocateElem(LinkList L, ElemType e){
    LNode *P = L->next;    //p指向第一个结点
    //从第一个结点开始查找数据域为e的结点
    while(p!=NULL && p->data != e){
        p = p->next;
    }
    return p;           //找到后返回该结点指针，否则返回NULL
}
```
#### 求单链表的长度
```c++
int Length(LinkList L){
    int len=0;       //统计表长
    LNode *p = L;
    while(p->next != NULL){
        p = p->next;
        len++;
    }
    return len;
}
```
### 2.3.4单链表的建立
Step 1:初始化一个单链表
Step 2:每次取一个数据元素，插入到表头/表尾
#### 尾插法
每次将新节点插入到当前链表的表尾，所以必须增加一个尾指针r,使其始终指向当前链表的尾结点。好处：生成的链表中结点的次序和输入数据的顺序会一致。
```c++
LinkList List_TailInsert(LinkList& L) {
    int x; // 设ElemType为整型int
    L = new LNode; // 建立头结点(初始化空表)
    LNode* s, * r = L; // r为表尾指针
    cin >> x; // 输入要插入的结点的值
    while (x != 9999) { // 输入9999表示结束
        s = new LNode;
        s->data = x;
        r->next = s;
        r = s; // r指针指向新的表尾结点
        cin >> x;
    }
    r->next = NULL; // 尾结点指针置空
    return L;
}
```
#### 头插法
循环对头结点进行后插操作
**重要应用：链表的逆置**
```c++
LinkList List_HeadInsert(LinkList& L) {       //逆向建立单链表
    LNode* s;
    int x;
    L = new LNode; // 建立头结点
    L->next = NULL; // 初始为空链表，这步相较于尾插法不能少！

    cin >> x; // 输入要插入的结点的值
    while (x != 9999) { // 输入9999表结束
        s = new LNode; // 创建新结点
        s->data = x;
        s->next = L->next;
        L->next = s; // 将新结点插入表中，L为头指针
        cin >> x;
    }
    return L;
}
```
##### 链表的逆置
```c++
LNode *Inverse(LNode *L)
{
    LNode *p, *q;
    p = L->next;     //p指针指向第一个结点
    L->next = NULL;  //头结点指向NULL

    while (p != NULL){
        q = p;
        p = p->next;
        q->next = L->next;  
        L->next = q;
    }
    return L;
}
```
---
### 双链表
![alt text](image-10.png)
#### 双链表中节点类型的描述
```c++
typedef struct DNode{            //定义双链表结点类型
    ElemType data;               //数据域
    struct DNode *prior, *next;  //前驱和后继指针
}DNode, *DLinklist;
```
#### 双链表的初始化（带头结点）
```c++
//初始化双链表
bool InitDLinkList(DLinklist &L) {
    L = new DNode;      //分配一个头结点
    if (L == NULL)                              //内存不足，分配失败
        return false;

    L->prior = NULL;   //头结点的prior指针永远指向NULL
    L->next = NULL;    //头结点之后暂时还没有结点
    return true;
}

void testDLinkList() {
    //初始化双链表
    DLinklist L;         // 定义指向头结点的指针L
    InitDLinkList(L);    //申请一片空间用于存放头结点，指针L指向这个头结点
    //...
}

//判断双链表是否为空
bool Empty(DLinklist L) {
    if (L->next == NULL)    //判断头结点的next指针是否为空
        return true;
    else
        return false;
}
```
#### 双链表的插入
后插操作,InsertNextDNode(p, s): 在p结点后插入s结点
```c++
bool InsertNextDNode(DNode *p, DNode *s){ //将结点 *s 插入到结点 *p之后
    if(p==NULL || s==NULL) //非法参数
        return false;
    
    s->next = p->next;
    if (p->next != NULL)   //p不是最后一个结点(p有后继结点)  
        p->next->prior = s;
    s->prior = p;
    p->next = s;
    
    return true;
}
```
#### 双链表的删除
删除p节点的后继节点
```c++
// 删除p结点的后继结点
bool DeletNextDNode(DNode *p) {
    if (p == NULL) return false;
    DNode *q = p->next;            // 找到p的后继结点q
    if (q == NULL) return false;     // p没有后继结点；
    p->next = q->next;
    if (q->next != NULL)           // q结点不是最后一个结点
        q->next->prior = p;
    delete q;

    return true;
}

// 销毁一个双链表
bool DestoryList(DLinklist &L) {
    // 循环释放各个数据结点
    while (L->next != NULL) {
        DeletNextDNode(L);  // 删除头结点的后继结点
        delete L; // 释放头结点
        L = NULL;  // 头指针指向NULL
    }
}
```
#### 双链表的遍历
前向遍历
```c++
while(p!=NULL){
    //对结点p做相应处理，eg打印
    p = p->prior;
}
```
后向遍历
```c++
while(p!=NULL){
    //对结点p做相应处理，eg打印
    p = p->next;
}
```
双链表不能随机存取，按位查找、按值查找操作都只能用遍历的方式实现，时间复杂度O(n)

---
### 循环链表
![alt text](image-11.png)
#### 循环单链表
最后一个结点的指针不是NULL,而是指向头结点
```c++
// 初始化一个循环单链表
bool InitList(LinkList &L) {
    L = new LNode; //分配一个头结点
    if (L == NULL) //内存不足，分配失败
        return false;
    L->next = L; //头结点next指针指向头结点
    return true;
}

// 判断循环单链表是否为空（终止条件为p或p->next是否等于头指针）
bool Empty(LinkList L) {
    if (L->next == L)
        return true; //为空
    else
        return false;
}

// 判断结点p是否为循环单链表的表尾结点
bool isTail(LinkList L, LNode *p) {
    if (p->next == L)
        return true;
    else
        return false;
}
```
- 单链表和循环单链表的比较：
- 单链表：
    - 从一个结点出发只能找到该结点后续的各个结点；
    - 对链表的操作大多都在头部或者尾部；
    - 设立头指针，从头结点找到尾部的时间复杂度=O(n)，即对表尾进行操作需要O(n)的时间复杂度;
- 循环单链表：
    - 从一个结点出发，可以找到其他任何一个结点；
    - 设立尾指针，从尾部找到头部的时间复杂度为O(1)，即对表头和表尾进行操作都只需要O(1)的时间复杂度;
#### 循环双链表
表头结点的prior指向表尾结点，表尾结点的next指向头结点。
```c++
// 初始化空的循环双链表
bool InitDLinkList(DLinklist &L) {
    L = new DNode; //分配一个头结点
    if (L == NULL) //内存不足，分配失败
        return false;
    L->prior = L; //头结点的prior指向头结点
    L->next = L; //头结点的next指向头结点
}

// 判断循环双链表是否为空
bool Empty(DLinklist L) {
    if (L->next == L)
        return true;
    else
        return false;
}

// 判断结点p是否为循环双链表的表尾结点
bool isTail(DLinklist L, DNode *p) {
    if (p->next == L)
        return true;
    else
        return false;
}
```
##### 循环双链表插入
```c++
//在p结点之后插入s结点
bool InsertNextDNode(DNode *p, DNode *s){ 
    s->next = p->next;
    p->next->prior = s;
    s->prior = p;
    p->next = s;
```
##### 循环双链表删除
```c++
//删除p的后继结点q
bool DeletNextDNode(DNode *p){
    p->next = q->next;
    q->next->prior = p;
    delete q;   
}
```
### (静态链表) 
![alt text](image-12.png)
- 单链表：各个结点散落在内存中的各个角落，每个结点有指向下一个节点的指针(下一个结点在内存中的地址);
- 静态链表：用数组的方式来描述线性表的链式存储结构: 分配一整片连续的内存空间，各个结点集中安置，包括了数据元素and下一个结点的数组下标(游标)
```c++
#define MaxSize 10        //静态链表的最大长度
 
struct Node{              //静态链表结构类型的定义
    ElemType data;        //存储数据元素
    int next;             //下一个元素的数组下标(游标)
};
 
//用数组定义多个连续存放的结点
void testSLinkList(){
    struct Node a[MaxSize];  //数组a作为静态链表, 每一个数组元素的类型都是struct Node
    //...
}
```
#### 插入位序为i的结点
- 找到一个空的结点，存入数据元素
- 从头结点出发找到位序为i-1的结点
- 修改新结点的next
- 修改i-1号结点的next
#### 删除某个结点
- 从头结点出发找到前驱结点
- 修改前驱结点的游标
-被删除结点next设为-2
---
## 顺序表v.s.链表
- 【逻辑结构】
    - 顺序表和链表都属于线性表，都是线性结构
- 【存储结构】
    - 顺序表：顺序存储
优点：支持随机存取，存储密度高
缺点：大片连续空间分配不方便，改变容量不方便
    - 链表：链式存储
优点：离散的小空间分配方便，改变容量方便
缺点：不可随机存取，存储密度低
- 【基本操作】
1. 创建
- 顺序表：需要预分配大片连续空间。若分配空间过小，则之后不方便拓展容量；若分配空间过大，则浪费内存资源；
- 静态分配：静态数组，容量不可改变
- 动态分配：动态数组，容量可以改变，但是需要移动大量元素，时间代价高（malloc(),free()）
- 链表：只需要分配一个头结点或者只声明一个头指针
2. 销毁
- 静态数组：系统自动回收空间
- 动态分配：动态数组——需要手动delete
3. 增/删
- 顺序表：插入/删除元素要将后续元素后移/前移；时间复杂度=O(n)，时间开销主要来自于移动元素；
- 链表：插入/删除元素只需要修改指针；时间复杂度=O(n)，时间开销主要来自查找目标元素
4. 查
- 顺序表
按位查找：O(1)
按值查找：O(n)，若表内元素有序，可在O($log_2^n$)时间内找到
- 链表
按位查找：O(n)
按值查找：O(n)
---
# 三.栈
- 栈是只允许在一端进行插入或删除操作的线性表
- 后进先出
- 题型：有哪些合法的出栈顺序
#### 栈的基本操作
- 创、销
InitStack(&S)：初始化栈。构造一个空栈 S，分配内存空间。
DestroyStack(&S)：销毁栈。销毁并释放栈 S 所占用的内存空间。
- 增、删
Push(&S, x)：进栈。若栈 S 未满，则将 x 加入使其成为新的栈顶元素。
Pop(&S, &x)：出栈。若栈 S 非空，则弹出（删除）栈顶元素，并用 x 返回。
- 查
GetTop(S, &x)：读取栈顶元素。若栈 S 非空，则用 x 返回栈顶元素。
- 其它
StackEmpty(S)：判空。断一个栈 S 是否为空，若 S 为空，则返回 true，否则返回 false。
#### 顺序栈的定义和基本操作
![alt text](image-13.png)
```c++
//定义
#define MaxSize 10              //定义栈中元素的最大个数
 
typedef struct{
    ElemType data[MaxSize];     //静态数组存放栈中元素
    int top;                    //栈顶指针
}SqStack;
 
void testStack(){
    SqStack S;                 //声明一个顺序栈(分配空间)
                               
}
```
```c++
// 初始化栈
void InitStack(SqStack &S){ 
    S.top = -1;                   //初始化栈顶指针为-1;也可设为0，这样top指向下一个可以插入的位置
}
 
// 判断栈是否为空
bool StackEmpty(SqStack S){    
    if(S.top == -1)        
        return true;    
    else        
        return false;
}
```
```c++
// 新元素进栈
bool Push(SqStack &S, ElemType x){        
    if(S.top == MaxSize - 1)// 栈满，报错；如果S.top初始化为0，则判断栈满：top == MaxSize        
        return false;    
    S.data[++S.top] = x; //指针先加1，新元素入栈 
    //S.data[S.top++] = x; top初始为0 
    return true;
}
 
// 出栈
bool Pop(SqStack &x, ElemType &x){       
    if(S.top == -1) // 栈空，报错        
        return false;    
    x = S.data[S.top--];
    // x = S.data[--S.top] S.top初始化为0    
    return true;
}
//数据还残留在内存中，只是逻辑上被删除了
```
```c++
// 读栈顶元素
bool GetTop(SqStack S, ElemType &x){        
    if(S.top == -1)                
        return false;        
    x = S.data[S.top];        
    return true; 
}
```
#### 链栈的定义和基本操作
- 链栈实际上就是一个只能采用头插法插入或删除数据的单链表;
```c++
typedef struct Linknode{        
    ElemType data;        //数据域    
    Linknode *next;       //指针域
}Linknode,*LiStack;
 
void testStack(){   
    LiStack L;            //声明一个链栈
}
```
```c++
// 初始化栈
bool InitStack(LiStack &L){    
    L = new Linknode;   
    if(L == NULL)             
        return false;   
    L->next = NULL;    
    return true;
}
 
// 判断栈是否为空
bool isEmpty(LiStack &L){    
    if(L->next == NULL)      
        return true;   
    else           
        return false;
}
```
```c++
// 新元素入栈
bool pushStack(LiStack &L, ElemType x) {
    Linknode *s = new Linknode;
    if (s == NULL)
        return false;
    s->data = x;
    // 头插法
    s->next = L->next;
    L->next = s;
    return true;
}

// 出栈
bool popStack(LiStack &L, int &x) {
    // 栈空不能出栈
    if (L->next == NULL)
        return false;
    Linknode *s = L->next;
    x = s->data;
    L->next = s->next;
    delete s;
    return true;
}
```
#### 栈的应用
##### ——1.括号匹配
![alt text](image-14.png)
- 实现
最后出现的左括号最先被匹配 （栈的特性——LIFO）。
遇到左括号就入栈。
遇到右括号，就“消耗”一个左括号（出栈）。
- 匹配失败情况：
扫描到右括号且栈空。
扫描完所有括号后，栈非空。
左右括号不匹配。
```c++
#define MaxSize 10 
typedef struct{    
    char data[MaxSize];   
    int top;
}SqStack;
//初始化栈 
void InitStack(SqStack &S);
//判断栈是否为空
bool StackEmpty(SqStack &S);
//新元素入栈
bool Push(SqStack &S, char x);
//栈顶元素出栈，用x返回
bool Pop(SqStack &S, char &x);
 
// 判断长度为length的字符串str中的括号是否匹配
bool bracketCheck(char str[], int length){ 
    SqStack S;      
    InitStack(S); 
    // 遍历str    
    for(int i=0; i<length; i++){   
        // 扫描到左括号，入栈     
        if(str[i] == '(' || str[i] == '[' || str[i] == '{'){    
            Push(S, str[i]);        
        }else{              
            // 扫描到右括号且栈空直接返回   
            if(StackEmpty(S))      
                return false;       
            char topElem;          
            // 用topElem接收栈顶元素   
            Pop(S, topElem);          
            // 括号不匹配           
            if(str[i] == ')' && topElem != '(' ) 
                return false;           
            if(str[i] == ']' && topElem != '[' )  
                return false;   
            if(str[i] == '}' && topElem != '{' )   
                return false;              }   
    }  
    // 扫描完毕若栈空则说明字符串str中括号匹配    
    return StackEmpty(S);
}
```
##### ——2.表达式求值问题
算术表达式由操作数、运算符、界限符“（”和“）”三个部分组成。
- **中缀表达式**：中缀表达式是一种通用的算术或逻辑公式表示方法，运算符以中缀形式处于操作数的中间。
对于计算机来说中缀表达式是很复杂的，因此计算表达式的值时，通常需要先将中缀表达式转换为前缀或后缀表达式，然后再进行求值。
- **后缀表达式**（逆波兰表达式）：后缀表达式的运算符位于两个操作数之后。
- **前缀表达式**（波兰表达式）：前缀表达式的运算符位于两个操作数之前。
---
###### 中缀表达式转后缀表达式-手算
**步骤1**： 确定中缀表达式中各个运算符的运算顺序
**步骤2**： 选择下一个运算符，按照[左操作数 右操作数 运算符]的方式组合成一个新的操作数
**步骤3**： 如果还有运算符没被处理，继续步骤2
**注意**：只要左边的运算符能先计算，就优先算左边的 (这样可以保证运算顺序唯一)；
```c++
中缀：A + B - C * D / E + F
       ①   ④   ②   ③   ⑤     
后缀：A B + C D * E / - F +
```
###### 后缀表达式的计算—手算:
从左往右扫描，每遇到一个运算符，就让运算符前面最近的两个操作数执行对应的运算，合体为一个操作数。

---
###### 中缀表达式转后缀表达式-机算
初始化一个栈，用于保存暂时还不能确定运算顺序的运算符。
从左到右处理各个元素，直到末尾。可能遇到三种情况:
1.**遇到操作数**：直接加入后缀表达式。
2.**遇到界限符**：遇到“(”直接入栈；遇到“)”则依次弹出栈内运算符并加入后缀表达式，直到 弹出“(”为止。注意：“(”不加入后缀表达式。
3.**遇到运算符**：依次弹出栈中优先级高于或等于当前运算符的所有运算符，并加入后缀表达式， 若碰到“(” 或栈空则停止。之后再把当前运算符入栈。
###### 后缀表达式的计算—机算:
**步骤1**: 从左往后扫描下一个元素，直到处理完所有元素;
**步骤2**: 若扫描到操作数，则压入栈，并回到步骤1;否则执行步骤3;
**步骤3**: 若扫描到运算符，则弹出两个栈顶元素，执行相应的运算，运算结果压回栈顶，回到步骤1;

注意：先出栈的是“右操作数”；
若表达式合法，则最后栈中只会留下一个元素，就是最终结果。

#### 综合实现（中缀表达式的计算）
**--中缀转后缀机算+后缀表达式机算**
- 初始化两个栈，操作数栈和运算符栈；
- 若扫描到操作数，压入操作数栈；
- 若扫描到运算符或界限符，则按照“中缀转后缀”相同的逻辑压入运算符栈
(期间也会弹出运算符，每当弹出一个运算符时，就需要再弹出两个操作数栈的栈顶元素并执行相应运算，运算结果再压回操作数栈) 
---
##### ——3.在递归中的应用
- 函数调用的特点：最后被调用的函数最先执行结束
- 函数调用时，需要用一个栈存储：
    - 调用返回地址
    - 实参
    - 局部变量
- 递归调用时，
    - 每进入一层递归，就将递归调用所需信息压入栈顶
    - 每退出一层递归，就从栈顶弹出相应信息
- 缺点：太多层递归可能回导致栈溢出；有时可能会包含很多重复计算。
适合用“递归”算法解决：可以把原始问题转换为属性相同，但规模较小的问题。
可以自定义栈将递归算法改造成非递归算法。
![alt text](image-15.png)
---
# 四.队列
- 只允许在表的一端(队尾)插入，表的另一端(队头)进行删除操作的线性表。
- 先进先出
#### 队列的基本操作
- 创、销
InitQueue(&Q)：初始化队列，构造一个空队列Q。
ClearQueue(&Q)：销毁队列，并释放队列Q占用的内存空间。
- 增、删
EnQueue(&Qx)：入队，若队列Q未满，则将x加入使之成为新的队尾。
DeQueue(&Q&x)：出队，若队列Q非空，则删除队头元素，并用x返回。
- 查
GetHead(Q&x)：读队头元素，若队列Q非空则用x返回队头元素。
- 其它常用操作
QueueEmpty(Q)：判队列空，若队列Q为空返回true，否则返回false。
#### 队列的顺序存储
![alt text](<屏幕截图 2024-05-28 144600.png>)
```c++
//顺序队列的定义
#define MaxSize 10;     //定义队列中元素的最大个数
 
typedef struct{     
    ElemType data[MaxSize];   //用静态数组存放队列元素     
    int front, rear;          //队头指针和队尾指针
}SqQueue;
 
void test{     
    SqQueue Q;                //声明一个队列
}
```
```c++
// 顺序队列的初始化
void InitQueue(SqQueue &Q){    
    // 初始化时，队头、队尾指针指向0   
    // 队尾指针指向队尾元素后一个位置
    // 队头指针指向的是队头元素的数组下标
    Q.rear = Q.front = 0;
}
 
// 判断队列是否为空
bool QueueEmpty(SqQueue Q){     
    if(Q.rear == Q.front)            
        return true;   
    else          
        return false;
}

// 1判断队列是否已满(牺牲一个存储空间，将仅剩一个空位置的状态当作“满”状态)
(Q.rear+1)%MaxSize==Q.front//队尾指针的下一个位置是对头

// 2判断队列是否已满(设置一个入队或出队标志tag，每次删除操作成功时，都令tag=0;每次插入操作成功时，都令tag=1)
front == rear && tag == 1
```
注：取余运算：(Q.rear+1)%MaxSize; 将存储空间在逻辑上变成了环状，将无限的整数域映射到有限的整数集合{0，1，2，...,MaxSize-1}上。队列元素个数：(rear+MaxSize-front)%MaxSize
```c++
// 入队
bool EnQueue(SqQueue &Q, ElemType x){       
    // 如果队列已满直接返回
    if((Q.rear+1)%MaxSize == Q.front) 	//牺牲一个单元区分队空和队满   
        return false;    
    Q.data[Q.rear] = x;   
    Q.rear = (Q.rear+1)%MaxSize; 
    return true;
}
 
// 出队
bool DeQueue(SqQueue &Q, ElemType &x){    
    // 如果队列为空直接返回    
    if(Q.rear == Q.front)  
        return false;     
    x = Q.data[Q.front];  
    Q.front = (Q.front+1)%MaxSize;
    return true;
}

// 获取队头元素并存入x
bool GetHead(SqQueue &Q, ElemType &x){
    if(Q.rear == Q.front)      
        return false;
    x = Q.data[Q.front];  
    return true;
}
```
#### 队列的链式存储
- 链队列的定义
```c++
// 链式队列结点
typedef struct LinkNode{  
    ElemType data;    
    struct LinkNode *next;
}LinkNode;
 
// 链式队列
typedef struct{        
    LinkNode *front, *rear;// 头指针和尾指针 
    // int count;    计数变量
}LinkQueue;
```
- 初始化队列（带头结点）
```c++
void InitQueue(LinkQueue &Q) {
    // 初始化时，front、rear都指向头结点
    Q.front = Q.rear = new LinkNode;
    Q.front->next = NULL;
}

// 判断队列是否为空
bool IsEmpty(LinkQueue Q) {
    if (Q.front == Q.rear)
        return true;
    else
        return false;
}
```
- 入队、出队
```c++
//新元素入队
void EnQueue(LinkQueue &Q, ElemType x) {
    LinkNode *s = new LinkNode;
    s->data = x;
    s->next = nullptr;
    Q.rear->next = s;
    Q.rear = s;
}
//队头元素出队
bool DeQueue(LinkQueue &Q, ElemType &x) {
    if (Q.front == Q.rear)
        return false; //空队
    LinkNode *p = Q.front->next;
    x = p->data;//用变量x返回队头元素
    Q.front->next = p->next;//修改头结点的next指针
    if (Q.rear == p)
        Q.rear = Q.front;// 如果p是最后一个结点，则将rear指针也指向NULL
    delete p;//释放结点空间
    return true;
}
```
#### 双端队列
- 双端队列是允许从两端插入、两端删除的线性表。
- 如果只使用其中一端的插入、删除操作，则等同于栈。
- 输入受限的双端队列：允许一端插入，两端删除的线性表。
- 输出受限的双端队列：允许两端插入，一端删除的线性表。

题型：判断输出序列的合法化
#### 队列的应用
##### ——1.树的层次遍历
- 若树非空，则根结点入队；
- 若队列非空，队头元素出队并访问，同时将该元素的孩子依次入队；
- 重复以上操作直至队尾为空；
##### ——2.图的广度优先遍历
- 找到与顶点相邻的所有顶点；
- 未被访问过顶点入队尾；
- 改顶点出队。
##### ——3.在操作系统中的应用
操作系统中多个进程争抢着使用有限的系统资源时，先来先服务算法（First Come First Service）是是一种常用策略。

---
#### 数组的存储
- ![alt text](image-18.png)
 一维数组的存储：各数组元素大小相同，且物理上连续存放。设起始地址为LOC，则数组元素a[i]的存放地址 = LOC + i * sizeof(ElemType) (0≤i<10)
 - ![alt text](image-19.png)
   ![alt text](image-20.png)
    - M行N列的二维数组b[M][N]中，若按行优先存储，则b[i][j]的存储地址=LOC + （i*N+j）*sizeof(ElemType)
    - M行N列的二维数组b[M][N]中，若按列优先存储，则b[i][j]的存储地址=LOC + （j*M+i）*sizeof(ElemType)     
#### 矩阵的压缩存储
- **题型**：
    - 矩阵的压缩存储需要多长的数组
    - 由矩阵行列号<i,j>推出对应的数组下标号k
    - 由k推出<i,j>
    - 存储上三角/下三角、行优先/列优先、矩阵元素的下标从0/1开始、数组下标从0/1开始
![alt text](image-17.png)
- **普通矩阵**可用二位数组存储，描述矩阵元素时，行、列号通常从1开始。
- **对称矩阵**的压缩存储
    - 若n阶方阵中任意一个元素$a_{i,j}$,都有$a_{i,j}=a_{j,i}$则该矩阵为对称矩阵
    - 压缩存储策略：只存储主对角线+下三角区
    - 数组大小：$(n+1)*n\over 2$ 
    - 实现一个映射函数：矩阵下标$——>$ 一维数组下标。
    ![alt text](image-22.png)
- **三角矩阵**的压缩存储
    - 下三角矩阵：除了主对角线和下三角区，其余的元素都相同为一常量。
    上三角矩阵：除了主对角线和上三角区，其余的元素都相同为一常量。
    - 数组大小：${(n-1)*n\over 2}+1$ 
    ![alt text](image-23.png)
- **三对角矩阵**的压缩存储
    当$|i-j|>1$时，有$a_{i,j}$ =0($1\leqslant i,j\leqslant n$)
    - 数组大小：3n-2
    ![alt text](image-24.png)
- **稀疏矩阵**的压缩存储
    非零元素远远少于矩阵元素的个数
    ![alt text](image-25.png)
    ![alt text](image-26.png)
---
# 五.串
- 串，即**字符串 (String)** 是由零个或多个字符组成的有限序列。一般记为S='a1a2.....·an'(n>=0)
- 其中，S是串名，单引号括起来的字符序列是串的值;a~i~可以是字母、数字或其他字符;串中字符的个数n称为串的长度。n =0时的串称为空串 
```c++
例
S="HelloWorld!"
T='iPhone 11 Pro Max?'
```
子串:串中任意个连续的字符组成的子序列。
主串:包含子串的串。eg:T是子串'iphone'的主串
字符在主串中的位置:字符在串中的序号。
子串在主串中的位置:子串的第一个字符在主串中的位置。
空串V.S空格串 eg:M=''是空串，N='   '是由三个空格字符组成的空格串，每个空格字符占1B。
串是一种特殊的线性表，数据元素之间呈线性关系
串的数据对象限定为**字符集**（如中文字符、英文字符、数字字符、标点字符等）
串的基本操作，如增删改查等通常以**子串**为操作对象。
#### 串的基本操作
假设有串 T = '', S = 'iPhone 11 Pro Max?', W = 'Pro'

- StrAssign(&T, chars)： 赋值操作，把串T赋值为chars。
- StrCopy(&T, S):：复制操作，把串S复制得到串T。
- StrEmpty(S)：判空操作，若S为空串，则返回TRUE，否则返回False。
- StrLength(S)：求串长，返回串S的元素个数。
- ClearString(&S)：清空操作，将S清为空串。
- DestroyString(&S)：销毁串，将串S销毁（回收存储空间）。
- Concat(&T, S1, S2)：串联接，用T返回由S1和S2联接而成的新串。Concat(&T,S,W)后，T=“iPhone 11 Pro Max?Pro”
- SubString(&Sub, S, pos, len)求子串，用Sub返回串S的第pos个字符起长度为len的子串.   eg：执行SubString(&T,S,4,6)后，T=“one 11”
- Index(S, T)：定位操作，若主串S中存在与串T值相同的子串，则返回它再主串S中第一次出现的位置，否则函数值为0. eg:执行Index(S,W)后，返回值11
- StrCompare(S, T)：串的比较操作，参照英文词典排序方式；若S > T,返回值>0; S = T,返回值=0 (需要两个串完全相同) ; S < T,返回值<0.（从第一个字符开始往后依次对比，先出现更大字符的串就更大；长串的前缀与短串相同时，长串更大；只有两个串完全相同时才相等）
    - 每个字符在计算机中对应一个二进制数，比较字符的大小就是比较二进制数的大小。
---
#### 串的存储结构
##### 串的顺序存储
###### 静态数组实现(定长顺序存储)
```c++
#define MAXLEN 255   //预定义最大串长为255
typedef struct{
    char ch[MAXLEN];   //静态数组实现（定长顺序存储）;每个char字符占1B                    
    int length;        //串的实际长度
}SString;
```
######  动态数组实现( 堆分配存储)
```c++
typedef struct{
    char *ch;          //按串长分配存储区，ch指向串的基地址
    int length;        //串的实际长度
}HString;
HString S;
S.ch = new char[MAXLEN *sizeof(char)];
S.length = 0;
```
![alt text](image-27.png)
方案二：字符的位序和数组下标一一对应，但字符串的长度不能超过255
方案三：求串长度时，需要遍历
#### 串的链式存储
```c++
typedef struct StringNode{
    char ch; //每个结点存1个字符
    struct StringNode * next; 
}StringNode, * String; //缺点：每个字符1B，每个指针4B，存储密度低
//改善
typedef struct StringNode{
    char ch[4]; //每个结点存多个字符
    struct StringNode * next; 
}StringNode, * String; //每个结点没存满，可用#填充
```
#### 串的基本操作
```c++
#define MAXLEN 255
 
typedef struct{
    char ch[MAXLEN];   
    int length;       
}SString;
 
1. 求子串:用Sub返回串的第pos个字符起长度为len的字串
bool SubString(SString &Sub, SString S, int pos, int len){
    //子串范围越界
    if (pos+len-1 > S.length)
        return false;
    
    for (int i=pos; i<pos+len; i++)
        Sub.cn[i-pos+1] = S.ch[i];

    Sub.length = len;
    return true;
}
 
2. 比较两个串的大小:若S>T,则返回值>0；若S=T,则返回值=0
int StrCompare(SString S, SString T){
    for (int i; i<S.length && i<T.length; i++){
        if(S.ch[i] != T.ch[i])
            return S.ch[i] - T.ch[i];
    }
    //扫描过的所有字符都相同，则长度长的串更大
    return S.length - T.length;
}
 
3. 定位操作：若主串S中存在与串T值相同的子串，则返回它在主串S中第一次出现的位置；否则函数返回值为0
int Index(SString S, SString T){
    int i=1;
    n = StrLength(S);
    m = StrLength(T); //串T的长度
    SString sub;        //用于暂存子串
 
    while(i<=n-m+1){ //长度为n的主串中有多少个m长度的子串：n-m+1
        SubString(Sub,S,i,m);
        if(StrCompare(Sub,T)!=0)  ++i;
        else return i;    // 返回子串在主串中的位置
    }
    return 0;            //S中不存在与T相等的子串
}
```
#### 串的模式匹配算法
##### 串的朴素模式匹配
串的模式匹配：在**主串**中找到与**模式串**相同的子串，并返回其所在主串中的位置。
**朴素模式匹配算法(简单模式匹配算法) 思想:**
- 将主串中与模式串长度相同的子串搞出来，挨个与模式串对比当子串与模式串某个对应字符不匹配时，就立即放弃当前子串，转而检索下一个子串。
- 若模式串长度为m，主串长度为n，则直到匹配成功/匹配失败最多需要$(n-m+1)*m$ 次比较最坏时间复杂度: $0(nm)$
- 最坏情况:每个子串的前m-1个字符都和模式串匹配，只有第m个字符不匹配。
- 比较好的情况:每个子串的第1个字符就与模式串不匹配
```c++
方法1：
字符串的基本操作：Index(SString S, SString T)

方法2：
直接通过数组下标实现：
![alt text](image-29.png)
![alt text](image-28.png)
int Index(SString S, SString T){
    int i=1;                //扫描主串S
    int j=1;                //扫描模式串T
    while(i<=S.length && j<=T.length){
        if(S.ch[i] == T.ch[j]){
            ++i;
            ++j;             //继续比较后继字符
        }
        else{                //当前子串匹配失败
            i = i-j+2;      //主串指针i指向下一个子串的第一个位置
            j=1;             //模式串指针j回到模式串第一个位置
        }
    }
    if(j>T.length)          //当前子串匹配成功
        return i-T.length;  //返回当前子串第一个字符的位置
    else
        return 0;
}
``` 
##### KMP算法
- 朴素模式匹配算法的缺点:当某些子串与模式串能部分匹配时，主串的扫描指针 i 经常回溯，导致时间开销增加。最坏时间复杂度O(mn)。
- KMP算法:当子串和模式串不匹配时，主串指针i不回溯，模式串指针j = next[j]算法平均时间复杂度：O(m+n)
![alt text](image-30.png)
对于模式串T='abaabc'
当第6个元素匹配失败时，可令主串指针i不变，模式串指针j=3
当第5个元素匹配失败时，可令主串指针i不变，模式串指针j=2
当第4个元素匹配失败时，可令主串指针i不变，模式串指针j=2
当第3个元素匹配失败时，可令主串指针i不变，模式串指针j=1
当第2个元素匹配失败时，可令主串指针i不变，模式串指针j=1
当第1个元素匹配失败时，可令主串指针i不变，模式串指针j=0，i++，j++
![alt text](image-31.png)
**综上所述:**
进行KMP算法，先进行预处理：根据模式串T，求出next数组。
![alt text](image-32.png)
任何模式串都一样，第一个字符不匹配时，只能匹配下一个子串。因此，next[1]恒为0
任何模式串都一样，第二个字符不匹配时，应尝试匹配模式串的第一个字符。因此，next[2]恒为1
![alt text](image-33.png)
![alt text](image-34.png)
![alt text](image-35.png)
```c++
// 获取模式串T的next[]数组
void getNext(SString T, int next[]){ 
    int i=1, j=0;  //i表示当前处理的字符位置，j表示当前最长公共前后缀的长度
    next[1]=0;    //模式串的第一个字符没有前缀和后缀。
    while(i<T.length){   
        if(j==0 || T.ch[i]==T.ch[j]){ 
            ++i; ++j;      
            next[i]=j;  
        }else      
            j=next[j]; //跳过已经比较过的字符
    }

// KPM算法，求主串S中模式串T的位序，没有则返回0
int Index_KPM(SString S, SString T){   
    int i=1, j=1;  
    int next[T.length+1]; 
    getNext(T, next);  
    while(i<=S.length && j<=T.length){  
        if(j==0 || S.ch[i]==T.ch[j]){   
            ++i; ++j;   
        }else   
            j=next[j];   
    }    
    if(j>T.length)   
        return i-T.length;  
    else
        return 0;
}
最坏时间复杂度：O(m+n)。其中，求next数组O(m)，模式匹配过程最坏时间复杂度o(n)
```
![alt text](image-36.png)
先求next数组，再由next数组求nextval数组
```c++
void getNextval(SString T, int nextval[]){
    int i=1,j=0;
    nextval[1]=0;
    while(i<T.length){
        if(j==0 || T.ch[i]==T.ch[j]){
            ++i; ++j;
            if(T.ch[i]!=T.ch[j])
                nextval[i]=j;
            else
                nextval[i]=nextval[j];
        }else
            j=nextval[j];
    }
}
```
# 六.树
#### 树的基本概念
![alt text](image-37.png)
树是n（n≥0）个结点的有限集合,n=0时，称为空树。在任意一颗非空树中应满足：
- 有且仅有一个特定的称为根的节点.
- 当n>1时，其余结点可分为m (m >0) 个互不相交的有限集合T1,T2,...,Tm，其中每个集合本身又是一棵树，并且称为根结点的子树。
- 树是一种递归定义的数据结构（分为若干互不相交的子树，子树也有其根节点）
**结点之间的关系描述：**
![alt text](image-38.png)
- 祖先结点：沿路径到根节点所经过的所有结点。 eg:父亲，爷爷
- 子孙结点： eg：爷爷的子孙结点：父亲，二叔，三叔，你，F,G,H,I,J,K,L,M
- 双亲结点（父节点）：直接前驱
- 孩子结点：直接后继
- 兄弟结点：同一层同一个父节点下。 eg:你和F
- 两个结点之间的路径：只能从上往下
- 路径长度：经过几条边
**结点、树的属性描述**
- 结点的层次(深度)--从上往下数 eg:默认从1开始
- 结点的高度--从下往上数
- 树的高度 (深度)--总共多少层  eg:树高度为4
- 结点的度--有几个孩子(分支)  非叶子结点的度>0，叶子结点的度=0
- 树的度一-各结点的度的最大值
**有序树V.S无序树**
- 有序树--逻辑上看，树中结点的各子树从左至右是有次序的，不能互换
- 无序树--逻辑上看，树中结点的各子树从左至右是无次序的，可以互换
ps.选择什么结构，具体看你用树存什么，是否需要用结点的左右位置反映某些逻辑关系
**树V.S森林**
![alt text](image-39.png)
#### 树的基本性质
![alt text](image-40.png)
- 1: 树中的结点数=总度数+1
- 2:度为m的树、m叉树的区别：树的度--各结点的度的最大值；m叉树--每个结点最多只能有m个孩子的树
![alt text](image-41.png)
- 3: 度为m的树第 i 层至多有$m^{i-1}$个结点(i≥1)
![alt text](image-42.png)
- 4: 高度为h的m叉树至多有${m^h-1}\over m-1$个结点。 
由结论3结合等比数列求和可解。
- 5: 高度为h的m叉树至少有h个结点；高度为h、度为m的树至少有h+m-1个结点。
![alt text](image-43.png)
- 6: 具有n个结点的m叉树的最小高度为
![alt text](image-44.png)
#### 二叉树的基本概念
二叉树是n (n≥0)个结点的有限集合:
- 或者为空二叉树，即n =0。
- 或者由一个根结点和两个互不相交的被称为根的左子树和右子树组成。左子树和右子树又分别是一棵二叉树。

特点：
- 每个结点至多只有两棵子树
- 左右子树不能颠倒 (二叉树是有序树)
- 二叉树可以是空集合，根可以有空的左子树和空的右子树
![alt text](image-45.png)

**特殊二叉树**
![alt text](image-46.png)
- 满二叉树：一棵深度为k且有$2^{k-1}$个结点的二叉树称为满二叉树。
    - 每一层上的结点数都达到最大
    - 叶子全部在最低层。
    - 按层序从1开始编号，结点i的左孩子为 2i，右孩子为 2i+1;结点i的父节点为$\lfloor {i \over2} \rfloor$ (如果有的话)

![alt text](image-47.png)
- 完全二叉树：深度为k的具有n个结点的二叉树，当且仅当其每一个结点都与深度为k的满二叉树中编号为1~n的结点一一对应时，称之为完全二叉树
    - 只有最后两层可能有叶子结点
    - 最多只有一个度为1的结点
    - 按层序从1开始编号，结点i的左孩子为 2i，右孩子为 2i+1;结点i的父节点为$\lfloor {i \over2} \rfloor$ (如果有的话)
    - i≤$\lfloor {n \over2} \rfloor$为分支结点，i>$\lfloor {n \over2} \rfloor$为叶子结点
    - ps.如果某结点只有一个孩子，那么一定是左孩子

![alt text](image-48.png)
- 二叉排序树：具有如下性质的二叉树:
    - 左子树上所有结点的关键字均小于根结点的关键字;
    - 右子树上所有结点的关键字均大于根结点的关键字;
    - 左子树和右子树又各是一棵二叉排序树。
    - 二叉排序树可用于元素的排序、搜素，非常方便
- 平衡二叉树：树上任一结点的左子树和右子树的深度之差不超过1
用途：如果二叉排序树是平衡二叉树，可以得到更高的搜素效率
#### 二叉树的性质
- 1：设非空二叉树中度为0、1和2的结点个数分别为$n_0$、$n_1$和$n_2$，则$n_0=n_2+1$(叶子结点比二分支结点多一个)
推导：假设树中结点总数为n，则
①$n=n_0+n_1+n_2$ 
②$n=n_1+2n_2+1$(树的结点数=总度数+1)
- 2:![alt text](image-49.png)
- 3：对于完全二叉树，可以由总结点数 n 推出度为 0、1 和 2 的结点个数$n_0$、$n_1$、$n_2$
![alt text](image-50.png)
#### 二叉树的存储结构
##### 二叉树的顺序存储
![alt text](image-51.png)
可以让数组第一个位置空缺，保证数组下标和结点编号一致
```c++
#define MaxSize 100
 
struct TreeNode{
   ElemType value; //结点中的数据元素
   bool isEmpty;   //结点是否为空
}
 
main(){
   TreeNode t[MaxSize];
   //初始化所有结点标记为空
   for (int i=0; i<MaxSize; i++){
      t[i].isEmpty = true;
   }
}
```
![alt text](image-52.png)
![alt text](image-53.png)
二叉树的顺序存储结构一定要把二叉树的结点编号与完全二叉树对应起来。只适合存储完全二叉树，存储二叉树会造成空间的闲置与浪费
##### 二叉树的链式存储(常用)
```c++
//二叉树的结点
 
struct ElemType{
   int value;
};
 
typedef struct BiTnode{
   ElemType data;          //数据域
   struct BiTNode *lchild, *rchild; //左、右孩子指针
}BiTNode, *BiTree;
/*它为 struct BiTNode 结构体定义了一个别名 BiTNode。这意味着在此之后，你可以使用 BiTNode 而不是 struct BiTNode 来声明这种类型的结构体变量。例如，你可以写 BiTNode node; 而不是 struct BiTNode node;。

同时，它也为指向 struct BiTNode 的指针定义了一个别名 BiTree。这样，你可以使用 BiTree 来声明一个指向 BiTNode 结构体的指针。例如，你可以写 BiTree tree = &node;    */ 
//定义一棵空树
BiTree root = NULL;
 
//插入根节点
root = new BiTNode;
root -> data = {1};
root -> lchild = NULL;
root -> rchild = NULL;
 
//插入新结点
BiTNode *p = new BiTNode;
p -> data = {2};
p -> lchild = NULL;
p -> rchild = NULL;
root -> lchild = p; //作为根节点的左孩子
![alt text](image-54.png)
```
找到指定结点p的左右孩子非常方便，但找到其父节点只能从根开始遍历寻找
如果一个二叉树有n个结点，则共有2n个指针域，n-1个结点有指针，剩余n+1个空链域指向None,可以用于构造线索二叉树
 #### 二叉树的先/中/后序遍历
- 遍历：按照某种次序把所有结点都访问一遍。
- 层次遍历:基于树的层次特性确定的次序规则

**先序遍历:根左右(NLR)--前缀表达式**
```c++
void PreOrder(BiTree T){
   if(T!=NULL){
      visit(T);                 //访问根结点
      PreOrder(T->lchild);      //递归遍历左子树
      PreOrder(T->rchild);      //递归遍历右子树
   }
}
空间复杂度：O(h)
```
**中序遍历:左根右(LNR)--中缀表达式（需要加界限符）**
```c++
void InOrder(BiTree T){
   if(T!=NULL){
      InOrder(T->lchild);       //递归遍历左子树
      visit(T);                 //访问根结点
      InOrder(T->rchild);       //递归遍历右子树
   }
}
```
**后序遍历:左右根(LRN)--后缀表达式**
```c++
void PostOrder(BiTree T){
   if(T!=NULL){
      PostOrder(T->lchild);       //递归遍历左子树    
      PostOrder(T->rchild);       //递归遍历右子树
      visit(T);                 //访问根结点
   }
}
```
**二叉树的层序遍历**
①初始化一个辅助队列
②根结点入队
③若队列非空，则队头结点出队，访问该结点，并将孩子插入队尾(如果有的话)
④重复③直至队列为空
```c++
//二叉树的结点(链式存储)
typedef struct BiTnode{
   ElemType data;          
   struct BiTNode *lchild, *rchild; 
}BiTNode, *BiTree;
 
//链式队列结点
typedef struct LinkNode{
    BiTNode * data; //存指针而不是结点
    LinkNode *next;
}LinkNode;
 
typedef struct{
   LinkNode *front, *rear;  
}LinkQueue;
 
//层序遍历
void LevelOrder(BiTree T){
   LinkQueue Q;
   InitQueue (Q);          //初始化辅助队列
   BiTree p;
   EnQueue(Q,T);           //将根节点入队
   while(!isEmpty(Q)){     //队列不空则循环
      DeQueue(Q,p);        //队头结点出队
      visit(p);            //访问出队结点
      if(p->lchild != NULL)
         EnQueue(Q,p->lchild);   //左孩子入队
      if(p->rchild != NULL)
         EnQueue(Q,p->rchild);   //右孩子入队
   }
} 
```
#### 由遍历序列构造二叉树
若只给出一颗二叉树的前/中/后/层 序遍历序列中的一种，不能唯一确定一颗二叉树
- 1. 中序+前序遍历序列
![alt text](image-55.png)
- 2. 中序+后序遍历序列
![alt text](image-56.png)
- 3. 中序+层序遍历序列
![alt text](image-57.png)
---
#### 线索二叉树
- 线性表：给定任意一个元素的指针，就可以得到该元素后面的所有元素。而不是像二叉树只能从根节点开始遍历；要得到指定结点p在中序遍历序列中的前驱/后继，也只能从头进行一次中序遍历
- n个结点的二叉树，有 n+1 个空链域，可用来记录前驱、后继的信息。指向前驱、后继的指针被称为“线索”，形成的二叉树被称为线索二叉树。
- 中序线索化的存储
![alt text](image-58.png)
ps.前驱线索由左孩子指针充当
   后继线索由右孩子指针充当
   线索指向中序前驱、中序后继
- 先序线索化的存储
![alt text](image-59.png)
- 后序线索化的存储
![alt text](image-60.png)
-线索二叉树的存储结构
```c++
//线索二叉树结点
typedef struct ThreadNode{
   ElemType data;
   struct ThreadNode *lchild, *rchild;
   int ltag, rtag;                // 左、右线索标志
}ThreadNode, *ThreadTree;
tag==0,表示指针指向孩子
tag==1,表示指针指向线索
```
#### 二叉树的线索化 
中序线索化
```c++
//线索二叉树结点
typedef struct ThreadNode{
   int data;
   struct ThreadNode *lchild, *rchild;
   int ltag, rtag;                // 左、右线索标志
}ThreadNode, *ThreadTree;
 
//全局变量pre（可以在所有函数中进行修改）, 指向当前访问的结点的前驱
TreadNode *pre=NULL;

//中序线索化二叉树T
void CreateInThread(ThreadTree T){
   pre = NULL;                //pre初始为NULL
   if(T!=NULL);{              //非空二叉树才能进行线索化
      InThread(T);            //中序线索化二叉树
      if(pre->rchild == NULL)
         pre->rtag=1;         //遍历的最后一个结点的右指针在函数InThread中无法修改
   } 
}
//中序遍历二叉树，一边遍历一边线索化
void InThread(ThreadTree T){
    if(T!=NULL){
        InThread(T->lchild);    //中序遍历左子树
        visit(T);               //访问根节点
        InThread(T->rchild);    //中序遍历右子树
    }
}
 
void visit(ThreadNode *q){
   if(q->lchid = NULL){                 //左子树为空，建立前驱线索   
      q->lchild = pre;
      q->ltag = 1;
   }
 
   if(pre!=NULL && pre->rchild = NULL){ 
      pre->rchild = q;           //建立前驱结点的后继线索
      pre->rtag = 1;
   }
   pre = q;
}
```
前序线索化
```c++
typedef struct ThreadNode{
   int data;
   struct ThreadNode *lchild, *rchild;
   int ltag, rtag;                // 左、右线索标志
}ThreadNode, *ThreadTree;
 
TreadNode *pre=NULL;

void CreateInThread(ThreadTree T){
   pre = NULL;               
   if(T!=NULL);{              
      PreThread(T);           
      if(pre->rchild == NULL)
         pre->rtag=1;         
   }
}

void PreThread(ThreadTree T){
   if(T!=NULL){
      visit(T);
      if(T->ltag == 0)         //lchild不是前驱线索，避免循环
         PreThread(T->lchild);
      PreThread(T->rchild);
   }
}
 
void visit(ThreadNode *q){
   if(q->lchid = NULL){                   
      q->lchild = pre;
      q->ltag = 1;
   }
 
   if(pre!=NULL && pre->rchild = NULL){ 
      pre->rchild = q;           
      pre->rtag = 1;
   }
   pre = q;
}
```
后序线索化
```c++
typedef struct ThreadNode{
   int data;
   struct ThreadNode *lchild, *rchild;
   int ltag, rtag;            
}ThreadNode, *ThreadTree;
 
TreadNode *pre=NULL;
 
void PostThread(ThreadTree T){
   if(T!=NULL){
      PostThread(T->lchild);
      PostThread(T->rchild);
      visit(T);                 
   }
}
 
void visit(ThreadNode *q){
   if(q->lchid = NULL){                 
      q->lchild = pre;
      q->ltag = 1;
   }
 
   if(pre!=NULL && pre->rchild = NULL){ 
      pre->rchild = q;         
      pre->rtag = 1;
   }
   pre = q;
}
 
void CreateInThread(ThreadTree T){
   pre = NULL;               
   if(T!=NULL);{             
      PostThread(T);           
      if(pre->rchild == NULL)
         pre->rtag=1;         
   }
}
```
#### 线索二叉树找前驱/后继
![alt text](image-61.png)
![alt text](image-68.png)
**中序线索二叉树找到指定结点 * p 的中序后继 next：**
- ![alt text](image-65.png)
```c++
// 找到以p为根的子树中，第一个被中序遍历的结点
ThreadNode *FirstNode(ThreadNode *p){
    // 循环找到最左下结点（不一定是叶结点）
    while(p->ltag==0)
        p=p->lchild;
    return p;
}
 
// 在中序线索二叉树中找到结点p的后继结点
ThreadNode *NextNode(ThreadNode *p){
    // 右子树中最左下的结点
    if(p->rtag==0)
        return FirstNode(p->rchild);
    else
        return p->rchild;
}
 
// 对中序线索二叉树进行中序循环（非递归方法实现）  空间复杂度O(1)
void InOrder(ThreadNode *T){
    for(ThreadNode *p=FirstNode(T); p!=NULL; p=NextNode(p)){
        visit(p);
    }
}
```
**中序线索二叉树找到指定结点 * p 的中序前驱 pre：**
- ![alt text](image-64.png)
```c++
// 找到以p为根的子树中，最后一个被中序遍历的结点
ThreadNode *LastNode(ThreadNode *p){
    // 循环找到最右下结点（不一定是叶结点）
    while(p->rtag==0)
        p=p->rchild;
    return p;
}
 
// 在中序线索二叉树中找到结点p的前驱结点
ThreadNode *PreNode(ThreadNode *p){
    // 左子树中最右下的结点
    if(p->ltag==0)
        return LastNode(p->lchild);
    else
        return p->lchild;
}
 
// 对中序线索二叉树进行中序循环（非递归方法实现）
void RevOrder(ThreadNode *T){
    for(ThreadNode *p=LastNode(T); p!=NULL; p=PreNode(p))
        visit(p);
}
```
**先序线索二叉树找到指定结点 * p 的先序后继 next：**
- ![alt text](image-63.png)

**先序线索二叉树找到指定结点 * p 的先序前驱 pre：**
- 若p->ltag==1，则pre = p->lchild；
- 若p->ltag==0，要找到前驱可以从头开始先序遍历，或改用三叉链表，找到结点 * p 的父节点。
    - ![alt text](image-62.png)
    
**后序线索二叉树找到指定结点 * p 的后序前驱 pre：**
- ![alt text](image-66.png)

**后序线索二叉树找到指定结点 * p 的后序后继 next：**
- 若p->rtag==1，则next = p->rchild；
- 若p->rtag==0，要找到后继可以从头开始先序遍历，或改用三叉链表，找到结点 * p 的父节点。
    - ![alt text](image-67.png)
---

#### 树和森林
##### 树的存储结构
###### 双亲表示法（顺序存储）：每个结点中保存指向双亲的“指针”。
![alt text](image-69.png)
```c++
//数据域：存放结点本身信息。
//双亲域：指示本结点的双亲结点在数组中的位置。
#define MAX_TREE_SIZE 100  //树中最多结点数
 
typedef struct PTNode{      //树的结点定义
   ElemType data; 
   int parent;      //双亲位置域,指示的是数组下标
}PTNode;
 
typedef struct PTree{                   //树的类型定义
   PTNode nodes[MAX_TREE_SIZE];   //双亲表示
   int n;                         //结点数
}PTree;
```
**增：** 新增数据元素，无需按逻辑上的次序存储；（需要更改结点数n）
**删：（叶子结点）：**
方法① 将伪指针域设置为-1；（空数据导致遍历更慢）
方法②用后面的数据填补；（需要更改结点数n）
**优缺点:** 查指定结点的双亲很方便;查指定结点的孩子只能从头遍历,空数据导致遍历更慢.
###### 孩子表示法（顺序+链式存储）
孩子表示法:顺序存储各个节点，每个结点中保存孩子链表头指针。
![alt text](image-70.png)
###### 孩子兄弟表示法（链式存储）
**用孩子兄弟表示法可以将树转换为二叉树的形式**
```c++
typedef struct CSNode{
    ElemType data;
    struct CSNode *firstchild, *nextsibling;
}CSNode, *CSTree;
```
![alt text](image-71.png)
![alt text](image-72.png)
##### 森林和二叉树的转换
二叉链表存储森林--左孩子右兄弟
森林中各个树的根节点之间视为兄弟关系
![alt text](image-73.png)
![alt text](image-74.png)
##### 树和森林的遍历
###### 树的先根遍历
- 若树非空，先访问根结点，再依次对每棵子树进行先根遍历；（与对应二叉树的先序遍历序列相同）（深度优先遍历）
- 树的先根遍历序列与这棵树相应二叉树的先序序列相同。
```c++
void PreOrder(TreeNode *R){
   if(R!=NULL){
      visit(R);    //访问根节点
      while(R还有下一个子树T)
         PreOrder(T);      //先跟遍历下一个子树
   }
}
```
###### 树的后根遍历
- 若树非空，先依次对每棵子树进行后根遍历，最后再访问根结点。（深度优先遍历）
- 树的后根遍历序列与这棵树相应二叉树的中序序列相同。
```c++
void PostOrder(TreeNode *R){
   if(R!=NULL){
      while(R还有下一个子树T)
         PostOrder(T);      //后跟遍历下一个子树
      visit(R);    //访问根节点
   }
}
```
###### 树的层次遍历（广度优先遍历，用队列实现）
- 若树非空，则根结点入队；
- 若队列非空，队头元素出队并访问，同时将该元素的孩子依次入队；
- 重复以上操作直至队尾为空；
###### 森林的遍历
- 先序遍历：等同于依次对各个树进行先根遍历；也可以先转换成与之对应的二叉树，对二叉树进行先序遍历。
- 中序遍历：等同于依次对各个树进行后根遍历；也可以先转换成与之对应的二叉树，对二叉树进行中序遍历。
![alt text](image-75.png)
#### 应用-哈夫曼树
在含有n个带权叶结点的二叉树中，其中带权路径长度(WPL) 最小的二叉树，也称最优二叉树。
- 结点的权:有某种现实含义的数值(如:表示结点的重要性等)
- 结点的带权路径长度：从树的根到该结点的路径长度(经过的边数)与该结点上权值的乘积。
- 树的带权路径长度WPL:树中所有**叶结点**的带权路径长度之和 (WPL,Weighted Path Length)。

**哈夫曼树的构造**
给定n个权值分别为$w_1$, $W_2$,..., $w_n$,的结点，构造哈夫曼树的算法描述如下:
1) 将这n个结点分别作为n棵仅含一个结点的二叉树，构成森林F。
2) 构造一个新结点，从F中选取两棵根结点权值最小的树作为新结点的左、右子树，并且将新结点的权值置为左、右子树上根结点的权值之和。
3) 从F中删除刚才选出的两棵树，同时将新得到的树加入F中
4) 重复步骤2和3，直至F中只剩下一棵树为止。
**ps.**
- 每个初始结点最终都成为叶结点(前缀编码，解码无歧义)，且权值越小的结点到根结点的路径长度越大
- 哈夫曼树的结点总数为2n - 1
- 哈夫曼树中不存在度为1的结点。
- 哈夫曼树并不唯一，但WPL必然相同且为最优
- 固定长度编码：每个字符用相等长度的二进制位表示
- 可变长度编码：允许对不同字符用不等长的二进制位表示
- 若没有一个编码是另一个编码的前缀，则称这样的编码为前缀编码
---
# 七.图
#### 图的基本概念
![alt text](image-78.png)
![alt text](image-76.png)
图G由**顶点集V**和**边集E**组成，记为G=(V,E)，其中V(G)表示图G中顶点的有限非空集；E(G)表示图G中顶点之间的关系 (边) 集合。若V={V1, V2,...,Vn}，则用$|V|$表示图G中顶点的个数，也称图G的阶。E={(u, v) $u∈V$, $v∈V$}，用$|E|$表示图G中边的条数。
**线性表可以是空表，树可以是空树，但图不可以是空，V一定是非空集**
- 无向图和有向图
无向图：若E是无向边 （简称边) 的有限集合时，则图G为无向图。边是顶点的无序对，记为(v,w)或(w,v)，因为（v,w)=(w,v)，其中v、w是顶点。可以说顶点w和顶点v互为邻接点。边(v,w)依附于顶点w和v，或者说边(v,w)和顶点v、w相关联。
有向图：若E是有向边(也称弧)的有限集合时，则图G为有向图。弧是顶点的有序对，记为<v,w>，其中v、w是顶点，v称为**弧尾**，w称为**弧头**，<v.w>称为从顶点v到顶点w的弧，也称v邻接到w，或w邻接自v。<v, w> ≠ <w, v>
- 简单图和多重图
简单图：① 不存在重复边； ② 不存在顶点到自身的边。
多重图：图G中某两个结点之间的边数多于一条，又允许顶点通过同一条边和自己关联,则G为多重图。（数据结构课程不探讨本结构）
- 顶点的度
① 对于无向图：顶点v的度是指依附于该顶点的边的条数，记为TD(v)。
$\sum_{i=1}^n TD(V_i)=2|E|$
② 对于有向图：入度是以顶点v为终点的有向边的数目，记为ID(v);出度是以顶点v为起点的有向边的数目，记为OD(v)，顶点v的度等于其入度和出度之和，即TD(v) = ID(v) + OD(v)。
$\sum_{i=1}^n ID(V_i)=\sum_{i=1}^n OD(V_i)=|E|$
- 顶点-顶点的关系描述
**路径：** 顶点$v_p$,到顶点$v_q$之间的一条路径是指顶点序列。$v_p$,$v_{i1}$,$v_{i2}$,...,$v_{im},$$v_q$
**回路：** 第一个顶点和最后一个顶点相同的路径称为回路。
**简单路径:** 在路径序列中，顶点不重复出现的路径称为简单路径。
**简单回路：** 除第一个顶点和最后一个顶点外，其余顶点不重复出现的回路称为简单回路。
**路径长度：** 路径上边的数目。
**点到点的距离：** 从顶点u到顶点v的最短路径若存在，则此路径的长度为从u到v的距离。若从u到v不存在路径，则记该距离为无穷$(∞)$
**连通：** 无向图中，若从顶点v到顶点w有路径存在，则称v和w是连通的。
**强连通：** 有向图中，若从顶点v到顶点w和从顶点w到顶点v之间都有路径则称这两个顶点是强连通的。
**非连通图:** 若图G中任意两个顶点都是连通的，则称图G为连通图，否则称为非连通图。
对于n个顶点的无向图G，若G是连通图，则最少有$n-1$条边;若G是非连通图，则最多可能有$C_{n-1}^2$条边
**强连通图：** 若图中任何一对顶点都是强连通的，则称此图为强连通图。
对于n个顶点的有向图G，若G是强连通图，则最少有$n$条边（形成回路）
**图的局部-子图：** 设有两个图G=(V,E)和G'=(V',E'),若V'是V的子集，且E'是E的子集，则称G'是G的子图。
若有满足V(G')=V(G)的子图G'，则称其为G的生成子图
**连通分量：** 无向图的极大连通子图称为连通分量。（子图必须连通，包含尽可能多的顶点和边）
![alt text](image-77.png)
**强连通分量：** 有向图中的极大强连通子图称为有向图的强连通分量。
**连通图的生成树：** 包含图中全部顶点的一个极小连通子图。
若图中顶点数为n，则它的生成树含有 n-1 条边。对生成树而言，若砍去它的一条边，则会变成非连通图，若加上一条边则会形成一个回路。
**生成森林：** 在非连通图中，连通分量的生成树构成了非连通图的生成森林
**边的权：** 在一个图中，每条边都可以标上具有某种含义的数值，该数值称为该边的权值。
**带权图/网：** 边上带有权值的图称为带权图，也称网。
**带权路径长度：** 当图是带权图时，一条路径上所有边的权值之和，称为该路径的带权路径长度。
**特殊图：** 
无向完全图--无向图中任意两个顶点之间都存在边
有向完全图--有向图中任意两个顶点之间都存在方向相反的两条弧
稀疏图（边数很少）与稠密图
树--不存在回路，且连通的无向图
有向树--一个顶点的入度为0、其余顶点的入读均为1的有向图
**n个顶点的图，若|E|>n-1,则一定有回路**
#### 图的存储
##### 邻接矩阵
![alt text](image-79.png)
```c++
#define MaxVertexNum 100	//顶点数目的最大值

typedef struct{
	char Vex[MaxVertexNum];	//顶点表，存放顶点信息
	int Edge[MaxVertexNum][MaxVertexNum];	//邻接矩阵，边表。也可以用bool型或枚举型变量，表中只有0和1
	int vexnum, arcnum;	//图的当前顶点数和弧树
}MGraph;
```
**邻接矩阵法存储带权图**
![alt text](image-80.png)
```c++
#define MaxVertexNum 100	//顶点数目的最大值
#define INFINITY 最大的int值 //宏定义常量“无穷”

typedef struct{
	char Vex[MaxVertexNum];	//顶点表
	int Edge[MaxVertexNum][MaxVertexNum];	//边的权
	int vexnum, arcnum;	//图的当前顶点数和弧树
}MGraph;
```
**邻接矩阵法的性能分析**
空间复杂度：$O\left ( \left | V \right |^{2} \right )$，只和顶点数相关，和实际的边数无关。
数组实现的顺序存储，空间复杂度高，不适合存储稀疏图。
无向图的邻接矩阵是对称矩阵，可以压缩存储 (只存储上三角区或者下三角区)。
**邻接矩阵的性质：** 设图 G 的邻接阵为 A(矩阵元素为0或1)，则$A^{n}$的元素$A^{n}\left [ i \right ]\left [ j \right ]$等于由点i到顶点j的长度为n的路径的数目。
![alt text](image-81.png)
##### 邻接表
![alt text](image-82.png)
```c++
#define MAXVEXVertexnum 100	//图中顶点数目的最大值
type char VertexType;	//顶点类型应由用户定义
typedef int EdgeType;	//边上的权值类型应由用户定义

//边/弧
typedef struct ArcNode{
	int adjvex;	//该边/弧所指向的顶点的下标或者位置
	struct ArcNode *next;	//指向下一条弧的指针
    //EdgeType weight;      边权值
}ArcNode;
 
//顶点表结点
typedef struct VNode{
	VertexType data;	//顶点数据域
	ArcNode *first	//第一条边
}VNode, AdjList[MAXVEXVertexnum]; //一维数组存储各个顶点信息
 
//用邻接表存储的图
typedef struct{
	AdjList vertices;   //顶点结点的数组
	int vexnum, arcnum;	//图中当前顶点数和边数
} ALGraph;
```
![alt text](image-83.png)
ps.图的邻接表表示方式不唯一；图的邻接矩阵表示方式唯一

#### 图的基本操作
- Adjacent(G, x, y)：判断图 G 是否存在边 < x , y > 或 ( x , y )。
![alt text](image-84.png)![alt text](image-85.png)
Neighbors(G, x)：列出图 G 中与结点 x 邻接的边。
![alt text](image-86.png)![alt text](image-87.png)
- InsertVertex(G, x)：在图 G 中插入顶点 x 。
![alt text](image-88.png)
新顶点矩阵元素赋值为0在矩阵初始化就已完成。
- DeleteVertex(G, x)：从图 G 中删除顶点 x。
将待删除结点的矩阵全部赋0，增加bool型标志位用来标明是空元素
![alt text](image-89.png)![alt text](image-90.png)
- AddEdge(G, x, y)：若无向边 ( x , y )  或有向边 < x , y > 不存在，则向图 G 中添加该边。
![alt text](image-91.png)
- RemoveEdge(G, x, y)：若无向边 ( x , y )  或有向边 < x , y > 存在，则从图 G 中删除该边。
- **FirstNeighbor(G, x)：** 求图 G 中顶点 x 的第一个邻接点，若有则返回顶点号。若 x 没有邻接点或图中不存在 x，则返回 -1。
![alt text](image-92.png)
- **NextNeighbor(G, x, y)：** 假设图 G 中顶点 y 是顶点 x 的一个邻接点，返回除 y 之外顶点 x 的下一个邻接点的顶点号，若 y 是 x 的最后一个邻接点，则返回 -1。
![alt text](image-93.png)
- Get_edge_value(G, x, y)：获取图 G 中边 ( x , y )或 < x , y > 对应的权值。
- Set_edge_value(G, x, y, v)：设置图 G 中边 ( x , y )或 < x , y >对应的权值为 v。
时间开销在于找边

#### 图的遍历
![alt text](image-94.png)
![alt text](image-95.png)
##### 广度优先遍历 (Breadth-First-Search,BFS)
（1）找到与一个顶点相邻的所有顶点；
（2）标记哪些顶点被访问过；
（3）需要一个辅助队列。
![alt text](image-96.png)
```c++
邻接矩阵的广度遍历算法
bool visited[MAX_VERTEX_NUM]; //访问标记数组，判断某结点是否被访问
//解决问题：如果是非连通图，如何遍历完所有结点
void BFSTraverse(MGraph G){
	int i, j;
	Queue Q;
	for(i = 0; i<G.vexnum; ++i){
		visited[i] = FALSE;  //访问标记数组初始化
	}
	InitQueue(&Q);	//初始化一辅助用的队列
	for(i=0; i<G.vexnum; ++i){ //从0号顶点开始遍历
		//若是未访问过就处理
		if(!visited[i]) //对每个连通分量调用有一次BFS
            BFS(G,i);   //从i开始BFS
}

//广度优先遍历
void BFS(Graph G, int v){
    visit(v);   //访问初始顶点
    visited[v]=TRUE;//对V做已访问标记
    Enqueue(Q,v);   //顶点v入队列Q
    while(!isEmpty(Q)){
        DeQueue(Q,v);//顶点v出队列
        for(w=FirstNeighbor(G,v); w>=0; w= NextNeighbor(G,v,w)){
            //检测v所有邻接点
            if(!visited[w]){    //w为v的尚未访问的邻接顶点
                visit(w);       //访问顶点w
                visited[w]=TRUE; //对w做已访问标记
                EnQueue(Q,w);   //顶点w入队列
            }
        }
    }
}
对于无向图，调用BFS函数的次数=连通分量数
```
**复杂度分析** 
![alt text](image-97.png)
![alt text](image-98.png)
**广度优先生成树**
⼴度优先⽣成树由⼴度优先遍历过程确定。由于邻接表的表示⽅式不唯⼀，因此基于邻接表的⼴度优先⽣成树也不唯⼀。 邻接矩阵表示方式唯一，⼴度优先遍历序列也唯一。
![alt text](image-99.png)

##### 图的深度优先遍历（DFS）
```c++
bool visited[MAX_VERTEX_NUM];	//访问标记数组

void DFS(Graph G, int v){
	visit(v);	//访问顶点
	visited[v] = TRUE;	//设已访问标记
	for(int w = FirstNeighbor(G, v); w>=0; w=NextNeighor(G, v, w)){
		if(!visited[w]){	//w为u的尚未访问的邻接顶点
			DFS(G, w);
		}
	}
}
//如果是非连通图，则无法遍历完所有结点
void DFSTraverse(MGraph G){
	int v; 
	for(v=0; v<G.vexnum; ++v){
		visited[v] = FALSE;	//初始化已访问标记数据
	}
	for(v=0; v<G.vexnum; ++v){	//从v=0开始遍历
		if(!visited[v]){
			DFS(G, v);
		}
	}
}
```
**复杂度分析**
![alt text](image-100.png)
![alt text](image-101.png)
**深度优先遍历序列**
![alt text](image-102.png)
从 2 出发的深度优先遍历序列：2, 1, 5, 6, 3, 4, 7, 8
从 3 出发的深度优先遍历序列：3, 4, 7, 6, 2, 1, 5, 8
从 1 出发的深度优先遍历序列：1, 2, 6, 3, 4, 7, 8, 5
**深度优先生成树**
![alt text](image-103.png)
同⼀个图的邻接矩阵表示⽅式唯⼀，因此深度优先遍历序列唯⼀，深度优先⽣成树也唯⼀；
同⼀个图的邻接表表示⽅式不唯⼀，因此深度优先遍历序列不唯⼀，深度优先⽣成树也不唯⼀。
**深度优先⽣成深林：**
![alt text](image-104.png)
**图的遍历和连通性**
![alt text](image-105.png)
![alt text](image-106.png)

#### 图的应用
##### 最小生成树
- 生成树：连通图的生成树是包含图中全部顶点的一个极小连通子图。 若图中顶点数为 n，则它的生成树含有 n-1 条边。对生成树而言，若砍去它的一条边，则会变成非连通图，若加上一条边则会形成一个回路。
- 最⼩⽣成树（最⼩代价树）：对于一个带权连通无向图G =(V,E)，生成树不同，每棵树的权(即树中所有边上的权值之和)也可能不同。设R为G的所有生成树的集合，若T为R中边的权值之和最小的生成树，则T称为G的最小生成树(Minimum-Spannino-Tree,MST).
    - 最小生成树可能有多个，但边的权值之和总是唯一且最小的。
    - 如果一个连通图本身就是一棵树，则其最小生成树就是它本身。
    - 只有连通图才有生成树，非连通图只有生成森林。

**Prim算法** 从某一个顶点开始构建生成树;每次将代价最小的新顶点纳入生成树，直到所有顶点都纳入为止。时间复杂度: O($|V|^2$)适合用于边稠密图。
**Kruskal算法** 每次选择一条权值最小的边，使这条边的两头连通(原本已经连通的就不选)，直到所有结点都连通。时间复杂度: O($|E| log_2^{|E|}$ )适合用于边稀疏图。

##### 最短路径问题
![alt text](image-107.png)
**BFS算法**
```c++
#define MAX_LENGTH 2147483647			//地图中最大距离，表示正无穷
 
// 求顶点u到其他顶点的最短路径
void BFS_MIN_Disrance(Graph G,int u){
    for(i=0; i<G.vexnum; i++){
        visited[i]=FALSE;				//记录是否被访问过
        d[i]=MAX_LENGTH;				//用于记录顶点 u 到其他顶点的最短路径。
        path[i]=-1;						//记录最短路径从哪个顶点过来。
    }
    InitQueue(Q);						//初始化辅助队列
    d[u]=0; //起始顶点到自身距离设为0
    visites[u]=TREE;
    EnQueue(Q,u);
    while(!isEmpty[Q]){					//BFS算法主过程
        DeQueue(Q,u);					//队头元素出队并赋给u
        for(w=FirstNeighbor(G,u);w>=0;w=NextNeighbor(G,u,w)){
            if(!visited[w]){
                d[w]=d[u]+1;
                path[w]=u;
                visited[w]=TREE;
                EnQueue(Q,w);			//顶点w入队
            }
        }
    }
}
```
![alt text](image-108.png)

**Dijkstra算法**
带权路径长度--当图是带权图时，一条路径上所有边的权值之和，称为该路径的带权路径长度
![alt text](image-109.png)

![alt text](image-110.png)
![alt text](image-111.png)
![alt text](image-112.png)
![alt text](image-113.png)

**Floyd算法**
![alt text](image-114.png)
![alt text](image-115.png)
```c++
int dist[MaxVertexNum][MaxVertexNum];
int path[MaxVertexNum][MaxVertexNum];
 
void Floyd(MGraph G){
	int i,j,k;
    // 初始化部分
	for(i=0;i<G.vexnum;i++){
		for(j=0;j<G.vexnum;j++){
			dist[i][j]=G.Edge[i][j];		
			path[i][j]=-1;
		}
	}
    // 算法核心部分
	for(k=0;k<G.vexnum;k++){    //考虑以V_k作为中转点
		for(i=0;i<G.vexnum;i++){    //遍历整个矩阵，i为行号，j为列号
			for(j=0;j<G.vexnum;j++){
	   	    	if(dist[i][j]>dist[i][k]+dist[k][j]){ //以V_k为中转点的路径更短
	   		    	dist[i][j]=dist[i][k]+dist[k][j]; //更新最短路径长度
	   		    	path[i][j]=k;   //中转点
                }
			}
        }
    }
}
```

#### 有向无环图
若⼀个有向图中不存在环，则称为有向⽆环图，简称 DAG图（Directed Acyclic Graph）。
DGA描述表达式：
![alt text](image-116.png)
![alt text](image-117.png)
![alt text](image-118.png)
![alt text](image-119.png)
![alt text](image-120.png)
![alt text](image-121.png)

##### 拓扑排序
AOV网(Activity on Vertex Network，用顶点表示活动的网)：用DAG图(有向无环图)表示一个工程。顶点表示活动，有向边<$V_i,V_j$>表示活动$V_i$必须先于活动$V_j$进行。
![alt text](image-122.png)
- 从AOV网中选择一个没有前驱 (入度为0) 的顶点并输出
- 从网中删除该顶点和所有以它为起点的所有边。
- 重复1和2直到当前的AOV网为空或当前网中不存在无前驱的顶点为止

![alt text](image-123.png)
```c++
#define MaxVertexNum 100			//图中顶点数目最大值
 
typedef struct ArcNode{				//边表结点
    int adjvex;						//该弧所指向的顶点位置
    struct ArcNode *nextarc;		//指向下一条弧的指针
}ArcNode;
 
typedef struct VNode{				//顶点表结点
    VertexType data;				//顶点信息
    ArcNode *firstarc;				//指向第一条依附该顶点的弧的指针
}VNode,AdjList[MaxVertexNum];
 
typedef struct{
    AdjList vertices;				//邻接表
    int vexnum,arcnum;				//图的顶点数和弧数
}Graph;								//Graph是以邻接表存储的图类型
 
// 对图G进行拓扑排序
bool TopologicalSort(Graph G){
    InitStack(S);					//初始化栈，存储入度为0的顶点
    for(int i=0;i<g.vexnum;i++){
        if(indegree[i]==0)
            Push(S,i);				//将所有入度为0的顶点进栈
    }
    int count=0;					//计数，记录当前已经输出的顶点数
    while(!IsEmpty(S)){				//栈不空，则存入
        Pop(S,i);					//栈顶元素出栈
        print[count++]=i;			//输出顶点i
        for(p=G.vertices[i].firstarc;p;p=p=->nextarc){
            //将所有i指向的顶点的入度减1，并将入度为0的顶点压入栈
            v=p->adjvex;
            if(!(--indegree[v]))
                Push(S,v);			//入度为0，则入栈
        }
    }
    if(count<G.vexnum)              //排序失败,有向图中存在回路
        return false;				
    else
        return true;				//排序成功
}
```
##### 关键路径
AOE 网：在带权有向图中，以顶点表示事件，以有向边表示活动，以边上的权值表示完成该活动的开销（如完成活动所需的时间），称之为⽤边表示活动的⽹络，简称 AOE ⽹ (Activity On Edge NetWork)。
![alt text](image-124.png)
- 只有在某顶点所代表的事件发⽣后，从该顶点出发的各有向边所代表的活动才能开始；
- 只有在进⼊某顶点的各有向边所代表的活动都已结束时，该顶点所代表的事件才能发⽣。 另外，有些活动是可以并⾏进⾏的。
- 在 AOE ⽹中仅有⼀个⼊度为 0 的顶点，称为开始顶点（源点），它表示整个⼯程的开始； 也仅有⼀个出度为 0 的顶点，称为结束顶点（汇点），它表示整个⼯程的结束。  
    - 从源点到汇点的有向路径可能有多条，所有路径中，具有最⼤路径⻓度的路径称为关键路径，⽽把关键路径上的活动称为关键活动。
    - 完成整个⼯程的最短时间就是关键路径的⻓度，若关键活动不能按时完成，则整个 ⼯程的完成时间就会延⻓
![alt text](image-125.png)

1.求所有事件的最早发生时间ve(): ![alt text](image-126.png)
2.求所有事件的最迟发生时间 vl(): ![alt text](image-127.png)
3.求所有活动的最早发生时间 e(): 该活动弧的起点所表示的事件的最早发生时间
4.求所有活动的最迟发生时间 1(): 该活动弧的终点所表示事件的最迟发生时间与该活动所需时间之差
5.求所有活动的时间余量 d(): d() =l() - e(i)=最早-最迟。d(i)=0的活动就是关键活动，由关键活动可得关键路径
![alt text](image-128.png)

# 八.查找
- 查找：在数据集合中寻找满足某种条件的数据元素的过程称为查找。
- 查找表(查找结构)：用于查找的。数据集合称为查找表，它由同一类型的数据元素 (或记录)组成。
- 关键字：数据元素中唯一标识该元素的某个数据项的值，使用基于关键字的查找，查找结果应该是唯一的。
![alt text](image-129.png)
- 对查找表的常⻅操作：
查找符合条件的数据元素--静态查找表（仅关注查找速度即可）
插⼊、删除某个数据元素--动态查找表（也要关注插/删操作是否方便实现）
- 查找长度：在查找运算中，需要对比关键字的次数称为查找长度。
平均查找长度(ASL，Average Search Length)： 所有查找过程中进行关键字的比较次数的平均值。ASL的数量级反映了查找算法时间复杂度

#### 顺序查找
顺序查找，又叫“线性查找”，通常用于线性表算法。
```c++
typedef struct{				//查找表的数据结构（顺序表）
    ElemType *elem;			//动态数组基址
    int TableLen;			//表的长度
}SSTable;
 
int Search_Seq(SSTable ST,ElemType key){
    int i;
    for(i=0;i<ST.TableLen && ST.elem[i]!=key;++i);
    // 查找成功返回数组下标，否则返回-1
    	return i=ST.TableLen? -1 : i;
}
```
#### 折半查找
又称“二分查找”，仅适用于有序的顺序表
```c++
typedef struct{
    ElemType *elem;
    int TableLen;
}SSTable;
 
// 折半查找
int Binary_Search(SSTable L,ElemType key){
    int low=0,high=L.TableLen,mid;
    while(low<=high){
        mid=(low+high)/2;
        if(L.elem[mid]==key)
            return mid;
        else if(L.elem[mid]>key)
            high=mid-1;					//从前半部分继续查找
        else
            low=mid+1;					//从后半部分继续查找
    }
    return -1;
}
```
**折半查找判定树的构造：** $mid=\left \lfloor \right (low + high )/2 \rfloor$ ，如果当前 low 和 high 之间有奇数个元素，则 mid 分隔后，左右两部分元素个数相等；如果当前 low 和 high 之间有偶数个元素，则 mid 分隔后，左半部分⽐右半部分少⼀个元素。
对于任何⼀个结点，必有：右⼦树结点数 - 左⼦树结点数 = 0 或 1。
折半查找的判定树⼀定是平衡⼆叉树。折半查找的判定树中，只有最下⾯⼀层是不满的。
判定树结点关键字：左<中<右，满⾜⼆叉排序树的定义。失败结点：n+1个（等于成功结点的空链域数量）
树⾼$h=\left \lceil (n + 1 )/2 \right \rceil$。查找成功/失败的ASL≤h。时间复杂度 = $O\log_{2}n$ 。
####  分块查找
![alt text](<屏幕截图 2024-06-17 124141.png>)
#### 二叉排序树
![alt text](<屏幕截图 2024-06-17 124631.png>)
**二叉排序树的查找**
![alt text](<屏幕截图 2024-06-17 124844.png>) 

![alt text](<屏幕截图 2024-06-17 125037.png>)
**二叉排序树的插入**
![alt text](<屏幕截图 2024-06-17 125248.png>)
**二叉排序树的构造**
![alt text](<屏幕截图 2024-06-17 125508.png>)
**二叉排序树的删除**
左子树结点值<根结点值<右子树结点值
①若被删除结点是叶结点，则直接删除，不会破坏二叉排序树的性质
②若结点只有一颗左子树或右子树，则让结点的子树成为其父节点的子树
③![alt text](<屏幕截图 2024-06-17 130039.png>)
![alt text](<屏幕截图 2024-06-17 130019.png>)

#### 平衡二叉树
![alt text](<屏幕截图 2024-06-17 130402.png>)
**平衡二叉树的插入**
![alt text](<屏幕截图 2024-06-17 130659.png>)
插入/删除 很容易破坏“平衡”特性，需要频繁调整树的形态。如:插入操作导致平衡，则需要先计算平衡因子，找到最小不平衡子树 (时间开销大)，再进行LL/RR/LR/RL调整，则其它祖先结点都会恢复平衡。
LL:在A的左孩子的左子树中插入导致不平衡
![alt text](<屏幕截图 2024-06-17 131154.png>)
RR:在A的右孩子的右子树中插入导致不平衡
![alt text](<屏幕截图 2024-06-17 131419.png>)
![alt text](<屏幕截图 2024-06-17 131536.png>)
LR:在A的左孩子的右子树中插入导致不平衡
![alt text](<屏幕截图 2024-06-17 131918.png>)
![alt text](<屏幕截图 2024-06-17 131846.png>)
RL:在A的右孩子的左子树中插入导致不平衡
![alt text](<屏幕截图 2024-06-17 132008.png>)
![alt text](<屏幕截图 2024-06-17 132035.png>)

#### 散列表
散列表(Hash Table)，又称哈希表。是一种数据结构，特点是：数据元素的关键字与其存储地址直接相关。通过“哈希函数”：Addr=H(key)建立“关键字”与“存储地址”的联系。
![alt text](<屏幕截图 2024-06-17 134600.png>)

![alt text](<屏幕截图 2024-06-17 134713.png>)
**散列查找**
- 初始化：A d d r = H a s h ( k e y ) 
- 检测查找表中地址为 Addr 的位置上是否有记录，若无记录，返回查找失败；若有记录，比较它和 key 的值，若相等则返回查找成功，否则执行步骤③。
- 用给定的处理冲突方式计算“下一个散列表地址”，并把 Addr 置为此地址，转入步骤②。
**常见的散列函数**
- 直接定址法：直接取关键字的某个线性函数值为散列地址，散列函数为 H ( k e y ) = k e y  或 H ( k e y ) = a × k e y + b 。这种方法计算简单，不会产生冲突。缺点是空位较多，会造成存储空间浪费。
- 除留余数法：假定散列表表长 m，取一个不大于但最接近 m 的质数 p，利用散列函数 H ( k e y ) = k e y % p将关键字转换为散列地址。p取质数是因为这样可以使关键字通过散列函数转换后等概率地映射到散列空间上的任一地址。
- 数字分析法：假设关键字是 r进制数，而r个数码在个位上出现的频率不一定相同，可能在某些位上分布的均匀一些，而在某些位分布的不均匀。此时应选数码分布均匀的若干位作为散列地址。
- 平方取中法：这种方法取关键字平方值的中间几位作为散列地址，具体取多少位视具体情况而定。这种方法得到的散列地址与关键字的每一位都有关系，因此使得散列地址分布比较均匀。适用于关键字每位取值都不够均匀或均小于散列地址所需的位数。
**处理冲突的方法-开放地址法**
①线性探测法--发生冲突时，每次往后探测相邻的下一个单元是否为空
![alt text](<屏幕截图 2024-06-17 140319.png>)
为方便计算所要求的平均查找长度，需要知道每个元素的查找长度。为此，在放置每个元素到散列表的同时，将其搜索次数标注在元素的下方，这同时也是该元素的查找长度。
![alt text](ae7751272a493ba7613e9fe219b582c.jpg)
②链地址法
![alt text](image-131.png)

![alt text](image-130.png)

# 九.排序
- 排序：重新排列表中的元素，使表中元素满足按关键字有序的过程。
- 输入：n个记录$ \small R_{1},R_{2},...,R_{n}$，对应的关键字为 $\small k_{1},k_{2},...,k_{n} $。     
- 输出：输入序列的一个重排$\small R_{1}^{'},R_{2}^{'},...,R_{n}^{'}$ ，使得$\small k_{1}^{'}\leq k_{2}^{'}\leq ...\leq k_{n}^{'} $(也可递减)。
- 排序算法的评价指标：时间复杂度、空间复杂度、稳定性。
- 算法的稳定性：若待排序表中有两个元素$\small R_{1}$和$\small R_{2}$，其对应的关键字相同即$\small key_{i} = \small key_{j}$  ，且在排序前$\small R_{1}在\small R_{2}$的前面，若使用某一排序算法排序后，$\small R_{1}$仍然在$\small R_{2}$的前面，则称这个排序算法是稳定的，否则称排序算法是不稳定的。
- 分类：
内部排序： 排序期间元素都在内存中——关注如何使时间、空间复杂度更低。
外部排序： 排序期间元素无法全部同时存在内存中，必须在排序的过程中根据要求不断地在内、外存之间移动——关注如何使时间、空间复杂度更低，如何使读/写磁盘次数更少
#### 插入排序
每次将一个待排序的记录按其关键字大小，插入到前面已经排好序的子序列中，直到全部记录插入完成。 
![alt text](image-132.png)![alt text](image-133.png)
```c++
// 对A[]数组中共n个元素进行插入排序
void InsertSort(int A[],int n){
    int i,j,temp;
    for(i=1; i<n; i++){ //将各元素插入已排好序的序列中
        if(A[i]<A[i-1]){    	//如果A[i]关键字小于前驱
            temp=A[i];  
            for(j=i-1; j>=0 && A[j]>temp; --j)
                A[j+1]=A[j];    //所有大于temp的元素都向后挪
            A[j+1]=temp;
        }
    }
}
算法效率分析：
时间复杂度（对比关键字、移动元素）：最好情况(原始表已经有序) O(n)，最差情况（原始表为逆序）O(n^{2})，平均情况 O(n^{2})。
空间复杂度：O(1)。
算法稳定性：稳定。
适用性：适用于顺序存储和链式存储的线性表。
```
#### 希尔排序
先追求表中元素的部分有序，再逐渐逼近全局有序，以减小插入排序算法的时间复杂度。
希尔排序:先将待排序表分割成若干形如 $L[i,i+d,i+ed,...,i+kd] $的“特殊”子表，对各个子表分别进行直接插入排序。缩小增量d，重复上述过程，直到d=1为止。
![alt text](image-134.png)
![alt text](image-135.png)
![alt text](image-136.png)
![alt text](image-137.png)
![alt text](image-138.png)
```c++
// 对A[]数组共n个元素进行希尔排序
void ShellSort(ElemType A[], int n){
    int d,i,j;
    for(d=n/2; d>=1; d=d/2){  	//步长d递减
        for(i=d+1; i<=n; ++i){
            if(A[i]<A[i-d]){
                A[0]=A[i];		//A[0]做暂存单元
                for(j=i-d; j>0 && A[0]<A[j]; j-=d)
                    A[j+d]=A[j];
                A[j+d]=A[0];
            }
		}
    }
}
```
时间复杂度：希尔排序时间复杂度依赖于增量序列$d_1,d_2,...$的选择有关。最差情况O(n^{2})，n在某个特顶范围时可达O(n^^{1.3}) 。
空间复杂度：O(1)
算法稳定性：不稳定
仅适用于顺序表
#### 冒泡排序
从后往前（或从前往后）两两比较相邻元素的值，若为逆序（即 A [ i − 1 ] > A [ i ]) ，则交换它们，直到序列比较完。如此重复最多 n-1 次冒泡就能将所有元素排好序。为保证稳定性，关键字相同的元素不交换。
```c++
// 交换a和b的值
void swap(int &a, int &b){
    int temp=a;
    a=b;
    b=temp;
}
 
// 对A[]数组共n个元素进行冒泡排序
void BubbleSort(int A[], int n){
    for(int i=0; i<n-1; i++){
        bool flag = false; 			//标识本趟冒泡是否发生交换
        for(int j=n-1; j>i; j--){
            if(A[j-1]>A[j]){
                swap(A[j-1],A[j]);
                flag=true;
            }
        }
        if(flag==false)
            return;       //若本趟遍历没有发生交换，说明已经有序
    }
}
```
第n趟结束后，最小的n个元素会到最前边
![alt text](image-139.png)
时间复杂度：最好情况O(n) ，最差情况O(n^{2})，平均情况O(n^{2})。
空间复杂度：O(1)。
稳定性：稳定。
适用性：冒泡排序可以用于顺序表、链表（从前往后“冒泡”，每一趟将更大的元素“冒”到链尾）。
#### 快速排序
- $在待排序表 L [ 1... n ] 中任选一个元素 pivot 作为枢轴（通常取首元素），通过一趟排序将待排序表分为独立的两部分 L [ 1... k − 1 ] 和 L [ k + 1... n ] 。使得 L [ 1... k − 1 ] 中的所有元素小于 pivot，L [ k + 1... n ]中的所有元素大于等于 pivot，则 pivot 放在了其最终位置 L [ k ]上。重复此过程直到每部分内只有一个元素或空为止。$
- 快速排序是所有内部排序算法中性能最优的排序算法。
- 在快速排序算法中每一趟都会将枢轴元素放到其最终位置上。（可用来判断进行了几趟快速排序）
- 快速排序可以看作数组中n个元素组织成二叉树，每趟处理的枢轴是二叉树的根节点，递归调用的层数是二叉树的层数。
```c++
// 用第一个元素将数组A[]划分为两个部分
int Partition(int A[], int low, int high){
    int pivot = A[low]; //第一个元素作为枢轴
    while(low<high){    //用low、high搜索枢轴的最终位置
        while(low<high && A[high]>=pivot)
            --high;     //找到比枢轴小的元素，移到左端
        A[low] = A[high];
        while(low<high && A[low]<=pivot) 
            ++low;      //找到比枢轴大的元素，移到右端
        A[high] = A[low];
    }
    A[low] = pivot;
    return low;
} 
 
// 对A[]数组的low到high进行快速排序
void QuickSort(int A[], int low, int high){
    if(low<high){
        int pivotpos = Partition(A, low, high);  //划分
        QuickSort(A, low, pivotpos - 1);
        QuickSort(A, pivotpos + 1, high);
    }
}
```
算法效率分析：
$时间复杂度：快速排序的时间复杂度 = O ( n *递 归 调 用 的 层 数 ) 。最好情况 O(nlog_2^n),最差情况 O(n^2) ，平均情况O(n^2)。
空间复杂度：快速排序的空间复杂度 = O ( 递 归 调 用 的 层 数 ) 。最好情况O(log_2^n)，最差情况 O(n)，平均情况 O(n^2)。$
![alt text](image-140.png)
#### 直接选择排序(选择排序)
 **选择排序：** 每一趟在待排序元素中选取关键字最小（或最大）的元素加入有序子序列。
 n个元素的简单选择排序需要n-1趟处理
 ```c++
// 交换a和b的值
void swap(int &a, int &b){
    int temp = a;
    a = b;
    b = temp;
}
 
// 对A[]数组共n个元素进行选择排序
void SelectSort(int A[], int n){
    for(int i=0; i<n-1; i++){          	//一共进行n-1趟，i指向待排序序列中第一个元素
        int min = i;
        for(int j=i+1; j<n; j++){		//在A[i...n-1]中选择最小的元素
            if(A[j]<A[min])
                min = j;
        }
        if(min!=i)                     
            swap(A[i], A[min]);
    }
}
 ```
 $时间复杂度：无论待排序序列有序、逆序还是乱序，都需要进行 n-1 次处理，总共需要对比关键字(n−1)+(n−2)+. . .+1=n( n−1) /2 次，因此时间复杂度始终是O(n^{2}) 。$
空间复杂度：O(1) 。
稳定性：不稳定。
适用性：适用于顺序存储和链式存储的线性表。
#### 堆排序（选择排序）
![alt text](image-141.png)
首先将存放在 L [ 1... n ] 中的n个元素建成初始堆，由于堆本身的特点，堆顶元素就是最大值。将堆顶元素与堆底元素交换，这样待排序列的最大元素已经找到了排序后的位置。此时剩下的元素已不满足大根堆的性质，堆被破坏，将堆顶元素下坠使其继续保持大根堆的性质，如此重复直到堆中仅剩一个元素为止。（建堆、排序）
在顺序存储的完全二叉树中：
$非终端结点的编号 ：i ≤ \lfloor n/2 \rfloor;
i 的左右孩子 ：2i 和 2i+1
i 的父节点：[ i / 2 ]$
![alt text](image-142.png)
![alt text](image-143.png)
```c++
// 对初始序列建立大根堆
void BuildMaxHeap(int A[], int len){
    for(int i=len/2; i>0; i--) 		//从后往前调整所有非终端结点
        HeadAdjust(A, i, len);
}
 
// 将以k为根的子树调整为大根堆
void HeadAdjust(int A[], int k, int len){
    A[0] = A[k];                    //A[0]暂存子树的根结点
    for(int i=2*k; i<=len; i*=2){	//i初始化当前结点的左孩子                                 
        if(i<len && A[i]<A[i+1])	//沿k较大的子结点向下调整
            i++;                    //取key较大的子节点的下标
        if(A[0] >= A[i])
            break;                  //筛选结束
        else{
            A[k] = A[i];			//将A[i]调整至双亲结点上
            k=i;					//修改k值，以便继续向下筛选
        }
    }
    A[k] = A[0]                     //被筛选结点的值放入最终位置
}
 
// 交换a和b的值
void swap(int &a, int &b){
    int temp = a;
    a = b;
    b = temp;
}
 
// 对长为len的数组A[]进行堆排序
void HeapSort(int A[], int len){
    BuildMaxHeap(A, len);         	//初始建立大根堆
    for(int i=len; i>1; i--){      	//n-1趟的交换和建堆过程
        swap(A[i], A[1]);
        HeadAdjust(A,1,i-1);
    }
}
```
$算法效率分析：
时间复杂度：O(n\log_{2}n)。建堆时间 O(n) ，之后进行 n-1 次向下调整操作，每次调整时间复杂度为O(\log_{2}n)。
空间复杂度：O(1)。
稳定性：不稳定。$

#### 归并排序

归并（Merge）：把两个或多个已经有序的序列合并成一个新的有序表。k路归并每选出一个元素，需对比关键字k-1次。

**二路归并（二合一）**
![alt text](image-144.png)
![alt text](image-145.png)
---
![alt text](image-146.png)
```c++
// 辅助数组B
int *B= new int[n];

// A[low,...,mid]，A[mid+1,...,high]各自有序，将这两个部分归并
void Merge(int A[], int low, int mid, int high){
    int i,j,k;
    for(k=low; k<=high; k++)
        B[k]=A[k];
    for(i=low, j=mid+1, k=i; i<=mid && j<= high; k++){
        if(B[i]<=B[j])
            A[k]=B[i++];
        else
            A[k]=B[j++];
    }
    //当某一序列已经遍历完了，将没有归并完的部分复制到尾部
    while(i<=mid)
        A[k++]=B[i++];
    while(j<=high) 
        A[k++]=B[j++];
}
 
// 归并排序
void MergeSort(int A[], int low, int high){
    if(low<high){
        int mid = (low+high)/2;
        MergeSort(A, low, mid);
        MergeSort(A, mid+1, high);
        Merge(A,low,mid,high);     //归并
    }
}
```
![alt text](image-147.png)
![alt text](image-148.png)
算法是稳定的