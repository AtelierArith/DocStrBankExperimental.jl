```
DateTime(zdt::ZonedDateTime) -> DateTime
```

Construct a `DateTime` based on the "local time" representation of the provided `ZonedDateTime`.

!!! warning
    Any arithmetic performed on the returned `DateTime` will be timezone unaware and will not reflect an accurate local time if the operation would cross a DST transition.


See also: [`DateTime(::ZonedDateTime, ::Type{UTC})`](@ref).

# Example

```jldoctest
julia> zdt = ZonedDateTime(2014, 5, 30, 21, tz"America/New_York")
2014-05-30T21:00:00-04:00

julia> DateTime(zdt)
2014-05-30T21:00:00
```
