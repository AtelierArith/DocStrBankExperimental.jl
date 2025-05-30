```
sorted_ring_pixels(s, ℓₘₐₓ, [T=Float64])
```

Cover the sphere 𝕊² with $(ℓₘₐₓ+1)²-s²$ pixels distributed in rings provided by [`sorted_rings`](@ref); see that function's documentation for more description.

The returned quantity is a vector of 2-SVectors containing the spherical coordinates of each pixel.  See also [`sorted_ring_rotors`](@ref) for the corresponding `Rotor`s.
