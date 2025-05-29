```
Moments(; weight=EqualWeight())
```

最初の4つの非中心モーメント。

# 例

```
o = fit!(Moments(), randn(1000))
mean(o)
var(o)
std(o)
skewness(o)
kurtosis(o)
```
