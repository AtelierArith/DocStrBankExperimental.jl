```
interval_isapprox(a::Interval, b::Interval; kwargs)
```

Checks whether the intervals $a$ and $b$ are approximate equal, that is both their lower and upper bound are approximately equal.

### Keywords

Same of `Base.isapprox`

### Example

```jldoctest
julia> a = 1..2
[1, 2]

julia> b = a + 1e-10
[1, 2.00001]

julia> interval_isapprox(a, b)
true

julia> interval_isapprox(a, b; atol=1e-15)
false
```
