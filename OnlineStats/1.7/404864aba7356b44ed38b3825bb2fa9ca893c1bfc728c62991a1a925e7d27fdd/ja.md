```
OrderStats(b::Int, T::Type = Float64; weight=EqualWeight())
```

バッチサイズ `b` の平均順序統計。

# 例

```
o = fit!(OrderStats(100), randn(10^5))
quantile(o, [.25, .5, .75])

f = ecdf(o)
f(0)
```
