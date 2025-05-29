```
to_standard_form(Ψ::RegularizationProblem, b::AbstractVector)
```

Converts vector b to standard form using (Hansen, 1998)

Example Usage (Regular Syntax)

```julia
b̄ = to_standard_form(Ψ, b)
```

Example Usage (Lazy Syntax)

```julia
b̄ = @>> b to_standard_form(Ψ)
```
