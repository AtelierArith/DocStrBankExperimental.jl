```
binwalls(r::AbstractRange; first=true, last=true)::AbstractRange
```

If `r` is interpreted as a collection of bin centers, `binwalls` returns the bin boundaries.

```jldoctest
julia> using RangeHelpers: binwalls

julia> binwalls(0.0:2.0:10.0)
-1.0:2.0:11.0

julia> binwalls(0.0:2.0:10.0, first=false)
1.0:2.0:11.0

julia> binwalls(0.0:2.0:10.0, last=false)
-1.0:2.0:9.0
```

See also [`bincenters`](@ref).
