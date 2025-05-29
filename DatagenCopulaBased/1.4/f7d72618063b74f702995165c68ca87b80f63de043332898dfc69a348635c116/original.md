```
cormatgen_two_constant(n::Int, α::Real, β::Real)
```

Returns the correlation matrix of size n x n of correlations determined by two constants, first must be greater than the second.

```julia
julia> cormatgen_two_constant(6, 0.5, 0.1)
6×6 Array{Float64,2}:
 1.0  0.5  0.5  0.1  0.1  0.1
 0.5  1.0  0.5  0.1  0.1  0.1
 0.5  0.5  1.0  0.1  0.1  0.1
 0.1  0.1  0.1  1.0  0.1  0.1
 0.1  0.1  0.1  0.1  1.0  0.1
 0.1  0.1  0.1  0.1  0.1  1.0


 julia> cormatgen_two_constant(4, 0.5, 0.1)
 4×4 Array{Float64,2}:
  1.0  0.5  0.1  0.1
  0.5  1.0  0.1  0.1
  0.1  0.1  1.0  0.1
  0.1  0.1  0.1  1.0
```
