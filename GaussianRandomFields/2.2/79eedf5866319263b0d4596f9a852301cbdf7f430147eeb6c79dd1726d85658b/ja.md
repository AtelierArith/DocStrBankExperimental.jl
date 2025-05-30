```
Spherical(λ, [σ = 1], [p = 2])
```

相関長 `λ` を持つ球面共分散構造、（オプション）周辺標準偏差 `σ` および（オプション）`p`-ノルムとして定義されます。

$$
C(x, y) = \begin{cases} σ^2 \left(1 - \displaystyle\frac{3}{2}\frac{ρ}{λ} + \frac{1}{2}\left(\frac{ρ}{λ}\right)^3\right) & \text{for }ρ≤λ\\0 & \text{for }ρ>λ\end{cases}
$$

ここで $ρ = ||x - y||_p$ です。

# 例

```jldoctest
julia> Spherical(0.1)
spherical (λ=0.1, σ=1.0, p=2.0)

julia> Spherical(1.0, σ=2)
spherical (λ=1.0, σ=2.0, p=2.0)

```

関連情報: [`Exponential`](@ref), [`Linear`](@ref), [`Whittle`](@ref), [`Gaussian`](@ref), [`SquaredExponential`](@ref), [`Matern`](@ref)
