```
resize_supercell(sys::System, dims::NTuple{3, Int})
```

Creates a [`System`](@ref) with a given number of conventional unit cells in each lattice vector direction. Interactions, spins, and other settings will be inherited from `sys`.

Equivalent to:

```julia
reshape_supercell(sys, [dims[1] 0 0; 0 dims[2] 0; 0 0 dims[3]])
```

See also [`reshape_supercell`](@ref) and [`repeat_periodically`](@ref).
