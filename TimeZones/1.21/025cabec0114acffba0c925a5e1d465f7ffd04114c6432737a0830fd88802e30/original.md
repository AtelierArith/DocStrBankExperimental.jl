```
Date(zdt::ZonedDateTime) -> Date
```

Construct a `Date` based on the "local time" representation of the provided `ZonedDateTime`.

See also: [`Date(::ZonedDateTime, ::Type{UTC})`](@ref).

# Example

```jldoctest
julia> zdt = ZonedDateTime(2014, 5, 30, 21, tz"America/New_York")
2014-05-30T21:00:00-04:00

julia> Date(zdt)
2014-05-30
```
