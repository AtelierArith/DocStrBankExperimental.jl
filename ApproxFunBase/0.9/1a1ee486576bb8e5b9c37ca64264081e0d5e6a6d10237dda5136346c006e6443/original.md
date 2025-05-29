```
tocanonical(d, x)
```

Map the point `x` in `d` to a point in `DomainSets.canonicaldomain(d)`.

# Examples

```jldoctest
julia> tocanonical(0..0.5, 0)
-1.0

julia> tocanonical(0..0.5, 0.5)
1.0
```
