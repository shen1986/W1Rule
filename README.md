# W1代码规范
- 根据菜老师的提议，我总结下C#代码的一些开发规范。
- 主要是以大家自觉为主。核心的思想是。代码要整洁，简练，且有注释说明。

## 缩进层级
- 缩进层级非常重要，弄的不好，容易造成很多误解。
下这段代码 (为了演示,.这里故意修改了示例代码的缩进〕。

```C#
if (wl && wl.length){
            for (i = 0, 1 = wl.length; i < 1; ++i) {
        p = wl[i];
        type = Y.Lang.type(r[p]);
        if (s.hasOwnProperty(p)) { if (merge && type == 'object') {

    Y.mix(r(p], s{p]);
} else if (ov || !(p in r)) {
                    r[p] = s[p];
            }
        }
    }
}    
```

- 快速读憧这段代码井不容易。 这里的缩进并不统一,一眼看去 else 是对应到第 1
行的if语句。 但实际上这个 else 和代码第 5行的if语句相对应。 

```C#
if (wl && wl.length)
{
    for (i = 0, 1 = wl.length; i < 1; ++i)
    {
        p = wl[i];
        type = Y.Lang.type(r[p]);

        if (s.hasOwnProperty(p))
        {
            if (merge && type == 'object')
            {
                Y.mix(r[p], s[p]);
            }
            else if (ov || !(p in r))
            {
                r[p] = s[p];
            }
        }
    }
}
```

- 本项目使用[tab]进行缩进

## 行的长度
- 如果一行的内容太长，编辑窗口就会出现滚动条。这样不利于我们查看代码，也比较变扭。
我们应该规定我们一行的长度不要超过80个字符。超过80个字符应该折行。这是因为很多编辑器是
在80个字符以后出现滚动条
- 这条规则，是希望大家不要把一行写的太长。由于难以测量。以自觉为主。

## 空行

- 空行常常被忽略，代码看起来应该像一段一段可读的代码，而不是全部糅合在一块。拿缩进层级的例子来说

```C#
if (wl && wl.length)
{
    for (i = 0, 1 = wl.length; i < 1; ++i)
    {
        p = wl[i];
        type = Y.Lang.type(r[p]);
        if (s.hasOwnProperty(p))
        {
            if (merge && type == 'object')
            {
                Y.mix(r[p], s[p]);
            }
            else if (ov || !(p in r))
            {
                r[p] = s[p];
            }
        }
    }
}
```

- 给这段代码加上空行

```C#
if (wl && wl.length)
{

    for (i = 0, 1 = wl.length; i < 1; ++i)
    {
        p = wl[i];
        type = Y.Lang.type(r[p]);

        if (s.hasOwnProperty(p))
        {

            if (merge && type == 'object')
            {
                Y.mix(r[p], s[p]);
            }
            else if (ov || !(p in r))
            {
                r[p] = s[p];
            }
        }
    }
}
```

- 这样看上去能够更加流畅的阅读，一般来讲下面的场景添加空行是不错的注意
    + 在方法之间。
    + 在方法中的局部变量和第一条语句之间。
    + 在多行或则单行注释之前。
    + 在方法的逻辑片段之间插入空行，提高可读性。

## 命名
- C# 命名规则是为了让整个程序代码统一以增强其可读性而设置的。每一个单位在开发一个软件之前都会编写一份编码规范的文档。

- 常用的命名方法有两种，一种是 Pascal 命名法（帕斯卡命名法），另一种是 Camel 命名法（驼峰命名法）。

- Pascal 命名法是指每个单词的首字母大写；Camel 命名法是指第一个单词小写，从第二个单词开始每个单词的首字母大写。

1. 变量的命名规则
变量的命名规则遵循 Camel 命名法，并尽量使用能描述变量作用的英文单词。例如存放学生姓名的变量可以定义成 name 或者 studentName 等。另外，变量名字也不建议过长， 最好是 1 个单词，最多不超过 3 个单词。
```C#
string name = "shenxf";
string studentName = "shen1986";
```

2. 常量的命名规则
为了与变量有所区分，通常将定义常量的单词的所有字母大写。例如定义求圆面积的 n 的值，可以将其定义成一个常量以保证在整个程序中使用的值是统一的，直接定义成 PI 即可。
```C#
const int PI = 3.14;
static int PI = 3.14;
const int MAX_COUNT = 10;
static int MIN_COUNT = 1;
```

3. 类的命名规则
类的命名规则遵循 Pascal 命名法，即每个单词的首字母大写。例如定义一个存放学生信息的类，可以定义成 Student。
```C#
class Person {
    // 类的内部构造
}
```

4. 接口的命名规则
接口的命名规则也遵循 Pascal 命名法，但通常都是以 I 开头，并将其后面的每个单词的首字母大写。例如定义一个存放值比较操作的接口，可以将其命名为 ICompare。
```C#
interface ICompare {
    // 类的内部构造
}
```

5. 方法的命名规则
方法的命名遵循 Pascal 命名法，一般采用动词来命名。例如实现添加用户信息操作的方法，可以将其命名为 AddUser。
```C#
void AddUser() {
    // 类的内部构造
}
```

## 变量和函数

- 变量的命名前缀应该是名词，这能后和函数的命名规则区分开，函数应该以动词来做前缀。

```C#
// 好的写法
int count = 10;
string myName = "shenxf";
bool found = true;

// 不好的写法: 变量看起来像函数
int getCount = 10;
bool isFound = true;

// 好的写法
function getName() {
    return myName;
}

// 不好的写法
function theName() {
    return myName;
}

```

- 命名应该要尽量短小精干，例如，count，length和size一看就知道是数字类型，name，title，和message一看就知道是字符串类型
- i，j，k通常在循环处理中使用。
- 要经量避免写无意义的命名。

- 对于方法的命名，第一个单词应该是动词。下面是一些常见的约定

动词 | 含义 
-|-
can | 函数返回一个布尔值
has | 函数返回一个布尔值
is | 函数返回一个布尔值
get | 函数返回一个非布尔值
set | 函数用来保存一个值

- 按照上面的写法，可读性会很好

```C#

if (isEnabled())
{
    setName("shenxf");
}

if (getName() === "shenxf")
{
    doSomething();
}
```

## 注释
### 单行注释

```C#
// 这是一句单行注释
```

- 双斜杠后面最好预留一个空格
- 单行注释 有3中使用方法
    + 独占一行注释，用来解释下一行代码，这行注释之前总是有一个空行，且缩进层级和下一行代码保持一致
    + 在代码行的尾部的注释。代码结束到注释之间至少有一个缩进。注释（包括之前的代码部分）不应当超过单行的最大字符数限制，如果超过了，就应该将这行注释放在代码行上方。
    + 被注释掉的大段代码（编译器自带的批量注释多行代码）

- 单行注释不应该用于多行，除非是注释的大段代码。

```C#
// 好的写法
if (condition) {

    // 如果代码执行到这里，则表示通过了左右的安全性检查
    allowed();
}

// 不好的写法：注释之前没有空行
if (condition) {
    // 如果代码执行到这里，则表示通过了左右的安全性检查
    allowed();
}

// 不好的写法：错误的缩进
if (condition) {
// 如果代码执行到这里，则表示通过了左右的安全性检查
    allowed();
}

// 好的写法
var result = something + somethingElse; // somethingElse不应当取值为null

// 不好的写法：代码和注释之间没有间隔
var result = something + somethingElse;// somethingElse不应当取值为null

// 好的写法
// if (condition) {
//     dosomething();
//     thenDoSomethingElse();
// }

// 不好的写法:这里应当用多行注释
// 接下来的这段代码非常难，那么，让我详细的解释下
// 这段代码首先判断条件是否为真
// 。。。。。。。
if (condition) {
    // 如果代码执行到这里，则表示通过了左右的安全性检查
    allowed();
}
```

### 多行注释

- 合法的多行注释

```C#
/* 我的注释 */
/* 另一段注释
这个注释包含2行 */
/*
又是一段注释
这段注释同样包含2行
*/
```

- 这些注释都是合法但是看得不清晰，推荐使用类似于java的注释方法
- 第一是`/*`,最后一行是`*/`，当中每一行都以`*`开头，且空开一个空格

```C#
/*
 * 另一段注释
 * 这个注释包含2行
 */
```

- 多行注释应该和单行注释一样注释之前要有空行，注释用来说明下面行的代码，并与下一行保持同样的缩进

```C#
// 好的写法
if (condition) {

    /*
     * 如果代码执行到这里
     * 说明通过了所有安全性检查
     */
    allowed();
}

// 不好的写法：注释之前无空行
if (condition) {
    /*
     * 如果代码执行到这里
     * 说明通过了所有安全性检查
     */
    allowed();
}

// 不好的写法：星号之后没有空格
if (condition) {
    /*
     *如果代码执行到这里
     *说明通过了所有安全性检查
     */
    allowed();
}

// 不好的写法：错误的缩进
if (condition) {
/*
 * 如果代码执行到这里
 * 说明通过了所有安全性检查
 */
    allowed();
}

// 不好的写法：代码尾部不要用多行注释
var result = something + somethingElse; /*somethingElse不应当取值为null*/
```

### 使用注释

- 代码不够清晰时应该添加注释，代码很明了的时候不应该添加注释，有点画蛇添足。

```C#
// 不好的写法：注释并没有提供有价值的信息

// 初始化count
int count = 10;

// 好的写法

// 改变这个值可能会使它变成青蛙
vint count = 10;
```

- 因此，添加注释的原则是需要让代码变的更清晰的时候。

#### 难以理解的代码

- 难以理解的代码应该添加注释

```C#
// 好的写法

if (mode)
{

    /*
     * 当 mode 为2时
     * 用来执行原型合并的操作。。。。
     * 。。。。
     */
    if (mode === 2)
    {
        Y.mix(receiver.prototype, supplier.prototype, overwrite,
                whitelis, 0, merge);
    }

     /*
      * 根据模式的类型。。。
      * 。。。。
      */
    from = mode === 1 || mode === 3 ? supplier.prototype : supperlier;
    to   = mode === 1 || mode === 4 ? receiver.prototype : receiver;

    /*
     * .......
     * ......
     */
    if (!from || !to)
    {
        from = supperlier;
        to   = receiver;
    }
}
else
{
    from = supplier;
    to = receiver;
}
```

#### 可能被误认为错误的代码

- 团队里面会有一些好心人，自主的把一个看上去错误代码改正，但是这段错误的往往并不是错误的源头
- 修改了这段代码会导致另外的bug

```C#
while (element && (element = element[asix])) // 赋值操作
{
    if( (all || element[TAG_NAME]) &&
        (!fn || fn(element)) )
    {
        
        return element;
    }
}
```

- 在这里例子里面作者写明了他是赋值操作，虽然这不是一种标准用法，检测工具可能会检测出问题
- 很容易被误解成一个错误。这种注释就表明作者是有意为之。从而避免了不必要的误解。

### 文档注释

- 一般文档注释有多种格式，C#文档格式：
    + 多行注释以三个斜杠`///`开始，接下来是描述信息，其中`<param></param>`符号来表示一个或多个属性。
    + 它支持xml语法，也可以写html语法。有兴趣的可以自己研究下。

```C#
/// <summary>
/// 根据下标取得子菜单元素
/// </summary>
/// <param name="i">下标</param>
/// <returns>子元素</returns>
public override MenuComponent getChild(int i)
{
    return (MenuComponent)menuComponents[i];
}
```

- 你应当确保对如下的内容添加注释
    + 所有的方法
        * 应当对方法，期望的参数和可能的返回值添加注释描述。
    + 所有的构造函数
        * 应当对自定义类型和期望的参数添加注释描述。
    + 所有包含文档化方法的对象
        * 如果一个对象包含一个或多个附带文档注释的方法，那么这个对象也应当适当地针对文档生成工具添加文档注释。
        * 当然，注释的详细格式和用法最终还是由你所选择的文档生成工具决定的。

## 花括号的对齐方式

- C#的风格VS中自动支持所以不在这里强调，快捷键`Ctrl + k -> Ctrl + f`代码会自动格式化。
    + 风格是将左括号放置于块语句首行的下一行。
    ```C#
    if (condition)
    {
        doSomething();
    }
    else
    {
        doSomethingElse();
    }
    ```

## switch语句

- JavaScript中的`switch`语句的行为和在其他语言中是不一样的：switch语句中可以使用任意类型值，任何表达式都可合法地用于case从句。但在其他语言中则必须使用原始值和常量。

[返回顶部](#编程风格)

### 缩进
- C#的风格
```C#
    switch(condition)
    {
        case "first":
            // 代码
            break;

        case "second":
            // 代码
            break;

        case "third":
            // 代码
            break;
        
        default:
            // 代码
    }
```

- 独特之处
    + 每条`case`语句相对于`switch`关键字都缩进一个层级。
    + 从第二条豫剧开始，每条`case`语句前后各有一个空行。

### case语句的“连续执行”
- `case`后面不加`break`，就会连续执行下面的条件，这个成为很多系统bug的原罪。
- 但是还是有许多人接受这种连续执行的编程方法。但是逻辑一定要写的清晰。
```C#
    switch(condition)
    {

        // 明显的依次执行
        case "first":
        case "second":
            // 代码
            break;

        case "third":
            // 代码
            
            /* fall through */
        default:
            // 代码
    }
```
- 前面2行代码是个很明显的连续执行，这是合理的。
- `third`里面由于添加了注释，说明这是有意为之。这也是合理的。

### default
- 比较有争论的议题是，是否需要`default`，很多人不论何时都不省略`default`，尽管它什么也不做。
- 我觉得下面这种写法可以。就按照这种写法
```C#
    switch(condition)
    {
        case "first":
            // 代码
            break;

        case "second":
            // 代码
            break;

        default:
            // default中没有逻辑
    }
```

## 结束语
- 根据我以往的编代码的经验，规则怎么定，还是会有很多违反现象。除非做成检测工具。不改正就不能编译。
- 而且规则定的太死，一定程度会抹杀程序员的想象力。所以也要给出一定的自由度。关键的核心思想还是代码要整洁
当看到代码里面注释掉代码满天飞，空逻辑，无用代码到处都是，注释是完全无关的信息，这样代码一眼就让人非常担心
觉得会有质量问题。
- 代码的最高境界是要符合5大原则，如果分割成最小单元，关注点分离，职责单一。如何优雅写出漂亮的代码。想想水泥工和教堂的故事。我们不只是在埋代码，我们是在构建一个证券系统。
