```
AutoCov(b, T = Float64; weight=EqualWeight())
```

データストリームの型 `T` に対して、ラグ 0 から `b` までの自己共分散/相関を計算します。

# 例

```
y = cumsum(randn(100))
o = AutoCov(5)
fit!(o, y)
autocov(o)
autocor(o)
```
