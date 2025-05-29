```
bincenters(r::AbstractRange)::AbstractRange
```

If `r` is interpreted as a collection of bin boundaries, `bincenters` returns the bin centers.

```jldoctest
julia> using RangeHelpers: bincenters

julia> bincenters(1:10.0)
1.5:1.0:9.5
```

See also [`binwalls`](@ref).
