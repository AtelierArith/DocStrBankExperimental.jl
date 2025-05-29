```
cormatgen_two_constant_noised(n::Int, α::Real, β::Real; ϵ::Real= (1-α)/2)
```

Returns the correlation matrix of size n x n  of correlations determined by two constants, first must be greater than the second. Additional noise is introduced by the parameter ϵ.

```julia
julia> Random.seed!(43);

julia> cormatgen_two_constant_noised(4, 0.5, 0.1)
4×4 Array{Float64,2}:
  1.0         0.314724   0.190368  -0.0530078
  0.314724    1.0       -0.085744   0.112183
  0.190368   -0.085744   1.0        0.138089
 -0.0530078   0.112183   0.138089   1.0
```
