```
set_pair_coupling_at!(sys::System, op, site1::Site, site2::Site; offset=nothing)
```

Sets an arbitrary coupling along the single bond connecting two [`Site`](@ref)s, ignoring crystal symmetry. Any previous coupling on this bond will be overwritten. The system must support inhomogeneous interactions via [`to_inhomogeneous`](@ref).

Use [`symmetry_equivalent_bonds`](@ref) to find `(site1, site2, offset)` values that would be symmetry equivalent to a given [`Bond`](@ref) in a homogeneous system. For smaller systems, the `offset` vector (in multiples of unit cells) will resolve ambiguities in the periodic wrapping.

The operator `op` may be provided as an anonymous function that accepts two spin dipole operators, or as a matrix that acts in the tensor product space of the two sites. The documentation for [`set_pair_coupling!`](@ref) provides examples constructing `op`.
