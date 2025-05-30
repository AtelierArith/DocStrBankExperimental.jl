```
SquaredExponential(λ, [σ = 1], [p = 2])
```

相関長 `λ`、（オプションの）周辺標準偏差 `σ` および（オプションの）`p`-ノルムを持つ二乗指数（ガウス）共分散構造は、次のように定義されます。

$$
C(x, y) = σ^2 \exp\left(-\left(\displaystyle\frac{ρ}{λ}\right)^2\right)
$$

ここで、$ρ = ||x - y||_p$ です。

# 例

```jldoctest
julia> SquaredExponential(0.1)
Gaussian (λ=0.1, σ=1.0, p=2.0)

julia> SquaredExponential(1, σ=2.)
Gaussian (λ=1.0, σ=2.0, p=2.0)

```

参照: [`Exponential`](@ref), [`Linear`](@ref), [`Spherical`](@ref), [`Whittle`](@ref), [`Gaussian`](@ref), [`Matern`](@ref)
