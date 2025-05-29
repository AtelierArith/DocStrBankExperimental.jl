```
cormatgen_toeplitz(n::Int, ρ::Real)
```

Returns the correlation matrix of size n x n of the Toeplitz structure with maximal correlation equal to ρ.

```julia
julia> cormatgen_toeplitz(5, 0.9)
5×5 Array{Float64,2}:
 1.0     0.9    0.81  0.729  0.6561
 0.9     1.0    0.9   0.81   0.729
 0.81    0.9    1.0   0.9    0.81
 0.729   0.81   0.9   1.0    0.9
 0.6561  0.729  0.81  0.9    1.0

julia> cormatgen_toeplitz(5, 0.6)
5×5 Array{Float64,2}:
 1.0     0.6    0.36  0.216  0.1296
 0.6     1.0    0.6   0.36   0.216
 0.36    0.6    1.0   0.6    0.36
 0.216   0.36   0.6   1.0    0.6
 0.1296  0.216  0.36  0.6    1.0
```
