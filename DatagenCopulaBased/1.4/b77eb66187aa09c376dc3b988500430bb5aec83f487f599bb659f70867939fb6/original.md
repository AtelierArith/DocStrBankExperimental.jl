```
cormatgen_toeplitz_noised(n::Int, ρ::Real; ϵ=(1-ρ)/(1+ρ)/2)
```

Returns the correlation matrix of size n x n of the Toeplitz structure with maximal correlation equal to ρ. Additiona noise id added by the ϵ parameter.

```julia
julia> Random.seed!(43);

julia> cormatgen_toeplitz_noised(5, 0.9)
5×5 Array{Float64,2}:
 1.0       0.89656   0.812152  0.720547  0.64318
 0.89656   1.0       0.918136  0.832571  0.734564
 0.812152  0.918136  1.0       0.915888  0.822804
 0.720547  0.832571  0.915888  1.0       0.903819
 0.64318   0.734564  0.822804  0.903819  1.0
```
