```
position_to_site(sys::System, r)
```

Converts a position `r` to four indices of a [`Site`](@ref). The coordinates of `r` are given in units of the lattice vectors for the original crystal. This function can be useful for working with systems that have been reshaped using [`reshape_supercell`](@ref).

# Example

```julia
# Find the `site` at the center of a unit cell which is displaced by four
# multiples of the first lattice vector
site = position_to_site(sys, [4.5, 0.5, 0.5])

# Print the dipole at this site
println(sys.dipoles[site])
```
