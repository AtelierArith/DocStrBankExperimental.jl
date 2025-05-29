```
to_general_form(Ψ::RegularizationProblem, b::AbstractVector, x̄::AbstractVector)
```

Converts solution $\bar {\rm x}$ computed in standard form back to general form  ${\rm x}$ using (Hansen, 1998).

$$
{\rm x}={\rm {\bf L^{+}_A}\bar{x} + x\_0}
$$

where the matrices and vectors are defined in [RegularizationProblem](@ref)

Example Usage (Regular Syntax)

```julia
x = to_general_form(Ψ, b, x̄) 
```

Example Usage (Lazy Syntax)

```julia
x = @>> x̄ to_general_form(Ψ, b) 
```
