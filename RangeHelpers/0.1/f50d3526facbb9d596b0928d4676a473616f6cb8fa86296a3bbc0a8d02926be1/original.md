```
asrange(itr; check=true, atol, rtol)::AbstractRange
```

Convert `itr` into a range, optionally validating the result.

```jldoctest
julia> using RangeHelpers

julia> asrange([1,2,3.0])
1.0:1.0:3.0

julia> asrange([1,2,3])
1:1:3

julia> asrange(1:3)
1:3

julia> asrange([1,2,4.0])
ERROR: ArgumentError: Cannot construct range from `itr`
itr = [1.0, 2.0, 4.0]
[...]

julia> asrange([1,2,4.0], atol=10)
1.0:1.5:4.0
```
