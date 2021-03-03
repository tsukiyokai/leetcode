## 题目

```
实现 strStr() 函数。
给定一个 haystack 字符串和一个 needle 字符串，在 haystack 字符串中找出 needle 字符串出现的第一个位置 (从 0 开始)。如果不存在，则返回  -1。

输入: haystack = "hello", needle = "ll"
输出: 2
```

## 解法

### 代码

```c++
class Solution {
public:
	int strStr(string haystack, string needle) {
		if (needle.size() > haystack.size()) return -1;
		if (needle.size() == 0) return 0;
		for (int i = 0; i < haystack.size() - needle.size() + 1; i++) {
			int j = i;
			bool flag = true;
			for (auto c : needle) {
				if (c == haystack[j]) j++;
				else {
					flag = false;
					break;
				}
			}
			if (flag) return i;
		}
		return -1;
	}
};
```

### 注释

```
第一个 for 循环写的很好，如此设置可以直接确保 needle 的尾巴不会超过 haystack 的末尾而发生上溢。
```

