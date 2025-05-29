```
set_kpoints!(calculation::Calculation{QE}, k_grid::NTuple{3, Int}; print=true)
set_kpoints!(calculation::Calculation{QE}, k_grid::NTuple{6, Int}; print=true)
set_kpoints!(calculation::Calculation{QE}, k_grid::Vector{<:NTuple{4}}; print=true, k_option=:crystal_b)
```

Convenience function to set the `:k_points` data block of `calculation`. The three different methods are targeted at `nscf`, `scf` or `vcrelax`, and `bands` calculations, respectively. For the `nscf` version an explicit list of `k_points` will be generated.

```
set_kpoints!(calculation::Calculation{Wannier90}, k_grid::NTuple{3, Int})
```

Similar to the `nscf` targeted function in the sense that it will generate an explicit list of `k_points`, adhering to the same rules as for the `nscf`. The `mp_grid` flag will also automatically be set.
