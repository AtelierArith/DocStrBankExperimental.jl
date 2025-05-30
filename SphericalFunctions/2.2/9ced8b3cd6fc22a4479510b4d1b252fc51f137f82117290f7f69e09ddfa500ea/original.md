```
sorted_ring_rotors(s, ℓₘₐₓ, [T=Float64])
```

Cover the sphere 𝕊² with $(ℓₘₐₓ+1)²-s²$ pixels distributed in rings provided by [`sorted_rings`](@ref); see that function's documentation for more description.

The returned quantity is a vector of `Rotor`s.  See also [`sorted_ring_rotors`](@ref) for the corresponding spherical coordinates.
