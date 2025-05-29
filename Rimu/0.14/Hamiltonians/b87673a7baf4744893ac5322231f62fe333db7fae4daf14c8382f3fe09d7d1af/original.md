```
shift_lattice(is)
```

Circular shift contiguous indices `is` in interval `[M÷2, M÷2)` such that set starts with 0, where `M=length(is)`.

Inverse operation: [`shift_lattice_inv`](@ref). Used in [`HubbardReal1DEP`](@ref) and [`HubbardMom1DEP`](@ref)
