```
sign(x::NumFieldElem, e::NumFieldEmb) -> Int
```

Given a number field element `x` and a complex embedding `e`, return `1`, `-1` or `0` depending on whether `e(x)` is positive, negative, or zero.

# Examples

```jldoctest
julia> K, a = quadratic_field(3);

julia> e = complex_embedding(K, 1.7);

julia> sign(a, e)
1
```
