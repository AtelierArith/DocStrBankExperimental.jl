```
Fun(f, d::Domain)
```

Return `Fun(f, Space(d))`, that is, it uses the default space for the specified domain.

# Examples

```jldoctest
julia> f = Fun(x->x^2, 0..1);

julia> f(0.1) ≈ (0.1)^2
true
```
