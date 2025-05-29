```
set_exchange_at!(sys::System, J, site1::Site, site2::Site; biquad=0, offset=nothing)
```

Sets an exchange interaction ``𝐒_i⋅J 𝐒_j` along the single bond connecting two [`Site`](@ref)s, ignoring crystal symmetry. Any previous coupling on this bond will be overwritten. The system must support inhomogeneous interactions via [`to_inhomogeneous`](@ref).

Use [`symmetry_equivalent_bonds`](@ref) to find `(site1, site2, offset)` values that would be symmetry equivalent to a given [`Bond`](@ref) in a homogeneous system. For smaller systems, the `offset` vector (in multiples of unit cells) will resolve ambiguities in the periodic wrapping.

See also [`set_exchange!`](@ref) for more details on specifying `J` and `biquad`. For more general couplings, use [`set_pair_coupling_at!`](@ref) instead.
