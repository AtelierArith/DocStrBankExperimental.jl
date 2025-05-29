```
≫(a::AbstractInterval, b::AbstractInterval) -> Bool
greater_than_disjoint(a::AbstractInterval, b::AbstractInterval) -> Bool
```

Greater-than-and-disjoint comparison operator. Returns `true` if `a` is greater than `b` and they are disjoint (they do not overlap).

```
julia> 10..20 ≫ 0..10
false

julia> 11..20 ≫ 0..10
true
```
