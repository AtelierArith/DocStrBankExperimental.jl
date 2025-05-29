```
density_from_matrix(ρmat::AbstractMatrix)
```

Construct density matrix in Pauli representation from matrix `ρmat`.

```jldoctest
julia> ρmat = 0.15 .*[ 1 -1; -1  1] + 0.35 .* [1 1; 1 1]; # create mixed state of + and -.
julia> ρ = density_from_matrix(ρmat)
DensityMatrix([1.0, 0.39999999999999997, 0.0, 0.0], 1)
```
