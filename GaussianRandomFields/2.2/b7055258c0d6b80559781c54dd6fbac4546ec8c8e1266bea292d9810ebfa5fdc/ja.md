```
Matern(λ, ν, [σ = 1], [p = 2])
```

マテーン共分散構造は、相関長 `λ`、滑らかさ `ν`、（オプションの）周辺標準偏差 `σ` および（オプションの）`p`-ノルムとして定義されます。

$$
C(x, y) = σ^2 \displaystyle\frac{2^{1 - ν}}{Γ(ν)} \left(\frac{ρ}{λ}\right)^ν K_ν\left(\frac{ρ}{λ}\right)
$$

ここで、$ρ = ||x - y||_p$ です。

# 例

```jldoctest
julia> Matern(0.1, 1.0)
Matérn (λ=0.1, ν=1.0, σ=1.0, p=2.0)

julia> Matern(1, 1, σ=2.0)
Matérn (λ=1.0, ν=1.0, σ=2.0, p=2.0)

```

参照: [`Exponential`](@ref), [`Linear`](@ref), [`Spherical`](@ref), [`Whittle`](@ref), [`Gaussian`](@ref), [`SquaredExponential`](@ref)
