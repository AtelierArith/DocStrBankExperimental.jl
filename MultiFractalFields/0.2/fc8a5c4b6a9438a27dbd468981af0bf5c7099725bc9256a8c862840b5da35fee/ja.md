```
Exponential(ξ, [λ = 1], [σ² = 1])
```

スケーリング指数 `ξ`、相関長 `λ` および分散 `σ²` を持つ指数共分散関数です。

これは $C(r)= \sigma^2  e^{-\left(\frac{r}{\lambda}\right)^{\xi}}$ と定義されます。

# 例

```jldoctest
julia> expcov = Exponential(0.5, 1.5, 3)
Exponential{Float64}(ξ=0.5, λ=1.5, σ²=3.0)

julia> expcov(0)
3.0

julia> expcov(1.5) == 3/ℯ
true
```
