```
TimeZone(str::AbstractString, mask::Class) -> TimeZone
```

Similar to [`TimeZone(::AbstractString)`](@ref) but allows you to control what time zone classes are allowed to be constructed with `mask`. Can be used to construct time zones which are classified as "legacy".

## Examples

```jldoctest
julia> TimeZone("US/Pacific")
ERROR: ArgumentError: The time zone "US/Pacific" is of class `TimeZones.Class(:LEGACY)` which is currently not allowed by the mask: `TimeZones.Class(:FIXED) | TimeZones.Class(:STANDARD)`

julia> TimeZone("US/Pacific", TimeZones.Class(:LEGACY))
US/Pacific (UTC-8/UTC-7)
```
