```
Exponential(λ, [σ = 1], [p = 2])
```

相関長 `λ` を持つ指数共分散構造、（オプション）周辺標準偏差 `σ` と（オプション）`p`-ノルムは次のように定義されます。

$$
C(x, y) = σ^2 \exp\left(-\displaystyle\frac{ρ}{λ}\right)
$$

ここで $ρ = ||x - y||_p$ です。

# 例

```jldoctest
julia> Exponential(0.1)
exponential (λ=0.1, σ=1.0, p=2.0)

julia> Exponential(1.0, σ=2)
exponential (λ=1.0, σ=2.0, p=2.0)

```

関連項目: [`Linear`](@ref), [`Spherical`](@ref), [`Whittle`](@ref), [`Gaussian`](@ref), [`SquaredExponential`](@ref), [`Matern`](@ref)
