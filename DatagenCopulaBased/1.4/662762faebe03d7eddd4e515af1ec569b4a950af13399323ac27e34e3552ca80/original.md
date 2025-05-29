```
cormatgen_constant_noised(n::Int, α::Real; ϵ::Real = (1 .-α)/2.)
```

Returns the constant correlation matrix of size n x n  with constant correlations equal to 0 <= α <= 1 and additinal noise determinde by ϵ.

```julia
julia> Random.seed!(43);

julia> cormatgen_constant_noised(3, 0.5)
3×3 Array{Float64,2}:
 1.0       0.506271  0.285793
 0.506271  1.0       0.475609
 0.285793  0.475609  1.0
```
