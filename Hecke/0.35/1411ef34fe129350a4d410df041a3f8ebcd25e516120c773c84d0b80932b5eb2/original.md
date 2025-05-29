```
number_field(p::InfPlc) -> NumField
```

Return the number field of the infinite place.

# Examples

```jldoctest
julia> K, = quadratic_field(5);

julia> p = infinite_places(K)[1];

julia> number_field(p) == K
true
```
