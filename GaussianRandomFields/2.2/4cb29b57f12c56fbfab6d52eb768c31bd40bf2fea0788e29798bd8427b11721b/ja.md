```
Gaussian(λ, [σ = 1], [p = 2])
```

相関長 `λ`、（オプションの）周辺標準偏差 `σ` および（オプションの）`p`-ノルムを持つガウス（平方指数）共分散構造は、次のように定義されます。

$$
C(x, y) = σ \exp\left(-\left(\displaystyle\frac{ρ}{λ}\right)^2\right)
$$

ここで、$ρ = ||x - y||_p$ です。

# 例

```jldoctest
julia> Gaussian(0.1)
Gaussian (λ=0.1, σ=1.0, p=2.0)

julia> Gaussian(1, σ=2.)
Gaussian (λ=1.0, σ=2.0, p=2.0)

```

関連項目: [`Exponential`](@ref), [`Linear`](@ref), [`Spherical`](@ref), [`Whittle`](@ref), [`SquaredExponential`](@ref), [`Matern`](@ref)
