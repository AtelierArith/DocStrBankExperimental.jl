```
angle(z)
```

Compute the phase angle in radians of a complex number `z`.

See also: [`atan`](@ref), [`cis`](@ref).

# Examples

```jldoctest
julia> rad2deg(angle(1 + im))
45.0

julia> rad2deg(angle(1 - im))
-45.0

julia> rad2deg(angle(-1 - im))
-135.0
```
