```
Variance(T = Float64; weight=EqualWeight())
```

単変量分散、型 `T` として追跡されます。

# 例

```
o = fit!(Variance(), randn(10^6))
mean(o)
var(o)
std(o)
```
