```
domain(f::Fun)
```

Return the domain that `f` is defined on.

# Examples

```jldoctest
julia> f = Fun(x->x^2);

julia> domain(f) == ChebyshevInterval()
true

julia> f = Fun(x->x^2, 0..1);

julia> domain(f) == 0..1
true
```
