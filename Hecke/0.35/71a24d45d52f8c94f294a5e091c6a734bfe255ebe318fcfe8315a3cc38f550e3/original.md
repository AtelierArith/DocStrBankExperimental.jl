```
is_real(p::InfPlc) -> Bool
```

Return whether the infinite place `p` is complex.

```jldoctest
julia> K, = quadratic_field(3);

julia> is_complex(infinite_places(K)[1])
false
```
