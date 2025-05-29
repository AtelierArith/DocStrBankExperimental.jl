```
to_standard_form(Ψ::RegularizationProblem, b::AbstractVector, x₀::AbstractVector)
```

ベクトル b と x₀ を標準形に変換します (Hansen, 1998)

使用例 (通常の構文)

```julia
b̄ = to_standard_form(Ψ, b, x₀)
```
