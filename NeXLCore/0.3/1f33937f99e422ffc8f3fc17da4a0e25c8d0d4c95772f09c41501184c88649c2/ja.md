`NormalizeBySubShell` は、サブシェルに関連付けられたすべての重みの合計を1に正規化します。

例:

```
sum(cxr=>weight(NormalizeBySubShell, cxr), characteristic(n"Fe", ltransitions))==1.0+1.0+1.0
```
