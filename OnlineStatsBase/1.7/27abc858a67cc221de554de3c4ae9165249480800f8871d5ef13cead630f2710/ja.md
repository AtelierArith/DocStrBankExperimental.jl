```
CovMatrix(p=0; weight=EqualWeight())
CovMatrix(::Type{T}, p=0; weight=EqualWeight())
```

`p`変数の共分散/相関行列を計算します。変数の数が不明な場合は、デフォルトの`p=0`を使用します。

# 例

```
o = fit!(CovMatrix(), randn(100, 4) |> eachrow)
cor(o)
cov(o)
mean(o)
var(o)
```
