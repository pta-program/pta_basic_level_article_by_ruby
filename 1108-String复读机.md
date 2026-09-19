# 1108 String复读机

- **分值：** 20分

### 题目描述

给定一个长度不超过 $10^4$ 的、仅由英文字母构成的字符串。请将字符重新调整顺序，按 `StringString....` （注意区分大小写）这样的顺序输出，并忽略其它字符。当然，六种字符的个数不一定是一样多的，若某种字符已经输出完，则余下的字符仍按 `String` 的顺序打印，直到所有字符都被输出。例如 `gnirtSSs` 要调整成 `StringS` 输出，其中 `s` 是多余字符被忽略。

### 输入格式：

输入在一行中给出一个长度不超过 $10^4$ 的、仅由英文字母构成的非空字符串。

### 输出格式：

在一行中按题目要求输出处理后的字符串。题目保证输出非空。

### 输入样例：
```
sTRidlinSayBingStrropriiSHSiRiagIgtSSr
```

### 输出样例：
```
StringStringSrigSriSiSii
```


### 解题思路

本题的核心是：统计 String 六个字符的数量，并按 String 的顺序循环输出仍有剩余的字符。程序先读取题目输入，再按照上述规则完成数据处理，最后严格按照题目要求输出结果。实现时应优先根据题目约束选择合适的数据类型和数据结构，避免溢出或不必要的重复计算。

时间复杂度为 O(L)；空间复杂度取决于输入规模，主要用于保存题目数据和中间结果。

### 代码流程说明

1. 读入字符串。
2. 统计 S,t,r,i,n,g 出现次数。
3. 按 String 顺序循环输出。

### 代码实现

```ruby
# 题目：1108-String复读机
# 实现原理：
# 本题的核心是：统计 String 六个字符的数量，并按 String 的顺序循环输出仍有剩余的字符
# 时间复杂度为 O(L)；空间复杂度取决于输入规模，主要用于保存题目数据和中间结果。
# 代码步骤：
# 1. 读取输入并初始化必要的数据结构。
# 2. 按题意完成核心计算，处理边界情况。
# 3. 按题目要求格式化并输出结果。
#
counts = STDIN.read.chars.tally
order = "String".chars
result = +""
while order.any? { |char| counts[char].to_i.positive? }
  order.each do |char|
    next unless counts[char].to_i.positive?
    result << char
    counts[char] -= 1
  end
end
puts result
```

### 代码流程图

```mermaid
flowchart TD
  A["开始"] --> B["读入字符串"]
  B --> C["统计 String 字符频次"]
  C --> D["按顺序循环输出"]
  D --> E["结束"]
```

### 解题流程图

```mermaid
flowchart TD
  A["输入文本"] --> B["像复读机一样输出 String"]
  B --> C["结束"]
```

### 常见易错点

- 只统计这 6 个字母，大小写按题面。
- 循环顺序 S-t-r-i-n-g。
- 没有则空输出。
