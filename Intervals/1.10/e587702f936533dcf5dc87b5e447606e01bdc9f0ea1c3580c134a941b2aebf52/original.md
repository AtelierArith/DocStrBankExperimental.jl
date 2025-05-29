```
≪(a::AbstractInterval, b::AbstractInterval) -> Bool
less_than_disjoint(a::AbstractInterval, b::AbstractInterval) -> Bool
```

Less-than-and-disjoint comparison operator. Returns `true` if `a` is less than `b` and they are disjoint (they do not overlap).

```
julia> 0..10 ≪ 10..20
false

julia> 0..10 ≪ 11..20
true
```
