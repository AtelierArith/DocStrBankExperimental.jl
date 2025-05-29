```
reshape_supercell(sys::System, shape)
```

Maps an existing [`System`](@ref) to a new one that has the shape and periodicity of a requested supercell. The columns of the $3×3$ integer matrix `shape` represent the supercell lattice vectors measured in units of the original crystal lattice vectors. Interactions, spins, and other settings will be inherited from `sys`.

In the special case that `shape` is a diagonal matrix, this function coincides with [`resize_supercell`](@ref).

See also [`repeat_periodically`](@ref).
