```
midcor(X, Y; c=9)
```

2つの変数間の相関を中分散と中共分散を使用して計算します。

$$
\frac{s_{xy}}{\sqrt{s_{xx} \cdot s_{yy}}}
$$

ここで、$s_{xx},s_{yy}$は各ベクトルの中分散であり、$s_{xy}$は2つのベクトルの中共分散です。

# 例

```jldoctest
julia> X = 10 .* randn(rng, 1000, 2) .+ 50;


julia> midcor(X[:, 1], X[:, 2])
-0.010827077678217934
```

# 参考文献

1. [Wikipedia](https://en.wikipedia.org/wiki/Biweight_midcorrelation)
2. [NIST: Biweight midcorrelation](https://www.itl.nist.gov/div898/software/dataplot/refman2/auxillar/biwmidcr.htm)

# 関連項目

[`midvar`](@ref), [`midcov`](@ref), [`scale`](@ref)
