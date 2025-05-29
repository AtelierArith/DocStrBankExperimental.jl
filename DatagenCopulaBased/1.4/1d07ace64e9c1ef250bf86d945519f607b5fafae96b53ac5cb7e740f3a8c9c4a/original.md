```
cormatgen_constant(n::Int, α::Real)
```

Returns the constant correlation matrix with constant correlations equal to 0 <= α <= 1

```julia
julia> cormatgen_constant(2, 0.5)
2×2 Array{Real,2}:
 1.0  0.5
 0.5  1.0
```
