```
bng2lonlat(e::T1, n::T2) where {T1<:Real, T2<:Real} -> longitude, latitude
```

Transform from `easting` and `northing` in m on the British National Grid to WGS84 `longitude` and `latitude` (degrees).

!!! note
    This function does not throw an error if `e` and `n` are outside the bounds of the National Grid.  Therefore this function should be used with caution.


# Example

```jldoctest
julia> bng2lonlat(175154, 225430)
(-5.268407238735794, 51.88199105278528)

```
