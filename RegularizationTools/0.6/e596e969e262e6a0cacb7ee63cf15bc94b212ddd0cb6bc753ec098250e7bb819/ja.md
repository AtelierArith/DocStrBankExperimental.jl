```
to_standard_form(Ψ::RegularizationProblem, b::AbstractVector)
```

ベクトル b を標準形に変換します (Hansen, 1998)

使用例 (通常の構文)

```julia
b̄ = to_standard_form(Ψ, b)
```

使用例 (遅延構文)

```julia
b̄ = @>> b to_standard_form(Ψ)
```
