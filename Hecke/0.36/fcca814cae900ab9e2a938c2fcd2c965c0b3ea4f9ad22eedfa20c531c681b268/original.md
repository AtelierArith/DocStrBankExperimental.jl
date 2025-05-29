```
is_negative(a::NumFieldElem, e::NumFieldEmb)   -> Bool
```

Given a number field element `a` and a real embedding `e`, return whether `a` is positive at `e`.

# Examples

```jldoctest
julia> K, a  = quadratic_field(5);

julia> e = complex_embedding(K, 2.1);

julia> is_negative(a, e)
false
```
