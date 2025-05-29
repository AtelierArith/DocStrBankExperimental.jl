```
RingName(ring)
```

Returns the name of the ring as a string.

```jldoctest
julia> ring = HomalgRingOfIntegers()
Integer ring

julia> RingName(ring)
"Z"

julia> field = HomalgFieldOfRationals()
Rational field

julia> RingName(field)
"Q"
```
