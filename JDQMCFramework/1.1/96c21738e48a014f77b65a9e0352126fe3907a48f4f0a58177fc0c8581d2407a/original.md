```
build_hopping_matrix!(
    K::AbstractMatrix{T},
    neighbor_table::Matrix{Int},
    t::AbstractVector{T}
) where {T<:Continuous}
```

Construct a hopping matrix `K` using `neighbor_table` along with the corresponding hopping amplitudes `t`. Each column of `neighbor_table` stores a pair of neighboring orbitals in the lattice, such that `size(neighbor_table,1) = 2`.
