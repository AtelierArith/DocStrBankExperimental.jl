```
CallFun(o::OnlineStat, f::Function)
```

OnlineStat `o` が更新されるたびに `f(o)` を呼び出します。

# 例

```
o = CallFun(Mean(), println)
fit!(o, [0,0,1,1])
```
