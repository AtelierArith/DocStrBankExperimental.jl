```
is_real(p::InfPlc) -> Bool
```

Return whether the infinite place `p` is real.

```jldoctest
julia> K, = quadratic_field(3);

julia> is_real(infinite_places(K)[1])
true
```
