```
signbit(x::Interval)
```

Returns an interval containing `true` (`1`) if the value of the sign of any element in `x` is negative, containing `false` (`0`) if any element in `x` is non-negative, and an empy interval if `x` is empty.

# Examples

```jldoctest
julia> signbit(@interval(-4))
[1, 1]

julia> signbit(@interval(5))
[0, 0]

julia> signbit(@interval(-4,5))
[0, 1]
```
