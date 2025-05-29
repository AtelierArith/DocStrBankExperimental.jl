```
in_wignerseitz(v::AbstractVector{<:Real}, c::Cell)  -->  Bool
```

Return whether the point `v` is inside the Wigner-Seitz cell `c`. 

The point `v` is assumed be provided in the same basis as the vertices of `c`.

If `c` and `v` are provided in the lattice basis (see [`setting`](@ref)), the function must first convert `c` and `v` to a Cartesian basis internally; accordingly, for repeated calls, it is recommended that `c` be provided in a Cartesian basis to avoid redundant conversions.
