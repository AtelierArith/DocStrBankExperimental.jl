```
function solve(
    Ψ::RegularizationProblem,
    b::AbstractVector,
    x₀::AbstractVector;
    alg = :gcv_svd,
    method = Brent(),
    λ₁ = 0.0001,
    λ₂ = 1000.0,
    λ₀ = 1.0,
    kwargs...
)
```

同様ですが、初期推定値 x₀ を含みます。使用例（遅延構文）

```julia
# A は行列で、b は応答ベクトルです。
sol = @> setupRegularizationProblem(A, 1) solve(b, x₀, alg = :L_curve, λ₂ = 10.0)
```
