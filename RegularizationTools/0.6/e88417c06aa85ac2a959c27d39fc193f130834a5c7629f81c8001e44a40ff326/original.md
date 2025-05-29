```
to_standard_form(Ψ::RegularizationProblem, b::AbstractVector, x₀::AbstractVector)
```

Converts vector b and x₀ to standard form using (Hansen, 1998)

Example Usage (Regular Syntax)

```julia
b̄ = to_standard_form(Ψ, b, x₀)
```
