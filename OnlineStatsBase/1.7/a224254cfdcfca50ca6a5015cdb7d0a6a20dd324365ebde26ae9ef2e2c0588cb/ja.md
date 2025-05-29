```
Mean(T = Float64; weight=EqualWeight())
```

単変量平均を追跡し、型 `T` として保存します。

# 例

```
@time fit!(Mean(), randn(10^6))
```
