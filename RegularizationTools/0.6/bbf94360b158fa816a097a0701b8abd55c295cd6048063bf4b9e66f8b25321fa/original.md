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

Same as above, but includes an initial guess x₀. Example Usage (Lazy Syntax)

```julia
# A is a Matrix and b is a response vector. 
sol = @> setupRegularizationProblem(A, 1) solve(b, x₀, alg = :L_curve, λ₂ = 10.0)
```
