```
symrange(;center=0, step, length, start, stop)
```

Construct a range, that is symmetric around center.

```jldoctest
julia> using RangeHelpers

julia> symrange(length=2, step=1)
-0.5:1.0:0.5

julia> symrange(length=3, step=1)
-1.0:1.0:1.0

julia> symrange(length=3, step=1, center=4)
3.0:1.0:5.0

julia> symrange(start=around(-4.1), step=2)
-4.0:2.0:4.0

julia> symrange(start=around(-4.1), step=2, center=1)
-4.0:2.0:6.0

julia> symrange(stop=around(4.1), step=2, center=1)
-2.0:2.0:4.0
```
