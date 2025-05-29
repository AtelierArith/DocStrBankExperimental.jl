```
shift_lattice_inv(js)
```

Circular shift indices starting with 0 into a contiguous set in interval `[M÷2, M÷2)`, where `M=length(js)`.

Inverse operation of [`shift_lattice`](@ref). Used in [`HubbardReal1DEP`](@ref) and [`HubbardMom1DEP`](@ref)
