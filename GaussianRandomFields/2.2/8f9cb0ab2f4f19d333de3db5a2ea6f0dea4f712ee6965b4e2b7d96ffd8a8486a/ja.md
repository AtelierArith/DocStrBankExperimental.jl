```
Linear(λ, [σ = 1], [p = 2])
```

相関長 `λ` を持つ線形共分散構造、（オプションの）周辺標準偏差 `σ` および（オプションの）`p`-ノルムとして定義されます。

$$
C(x, y) = \begin{cases} σ^2 \left(1 - \displaystyle\frac{ρ}{λ}\right) & \text{if }ρ ≤ λ\\ 0 & \text{if }ρ>λ\end{cases}
$$

ここで、$ρ = ||x - y||_p$ です。

# 例

```jldoctest
julia> Linear(0.1)
linear (λ=0.1, σ=1.0, p=2.0)

julia> Linear(1.0, σ=2)
linear (λ=1.0, σ=2.0, p=2.0)

```

関連項目: [`Exponential`](@ref), [`Spherical`](@ref), [`Whittle`](@ref), [`Gaussian`](@ref), [`SquaredExponential`](@ref), [`Matern`](@ref)
