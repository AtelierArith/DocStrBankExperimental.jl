```
e_plusmin(T, particle_symmetry::Type{<:Sector}, spin_symmetry::Type{<:Sector})
```

Return the two-body operator that creates a particle at the first site and annihilates a particle at the second. This is the sum of `e_plusmin_up` and `e_plusmin_down`.
