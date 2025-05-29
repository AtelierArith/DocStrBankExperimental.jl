```
unit(x::Dates.FixedPeriod)
unit(x::Type{<:Dates.FixedPeriod})
```

Return the units that correspond to a particular period.

# Examples

```jldoctest
julia> using Dates

julia> unit(Second(15)) == u"s"
true

julia> unit(Hour) == u"hr"
true
```
