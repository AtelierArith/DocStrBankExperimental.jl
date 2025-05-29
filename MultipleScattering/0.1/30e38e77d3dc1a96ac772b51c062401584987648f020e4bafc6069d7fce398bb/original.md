```
get_t_matrices(PhysicalMedium, Vector{Particles}, ω, basis_order::Integer)
```

Returns vector of T-matrices from a vector of particles in a specific domain. Can save computation if multiple of the same kind of particle are present in the vector.
