```
setdomain(f::Fun, d::Domain)
```

Return `f` projected onto `domain`.

!!! note
    The new function may differ from the original one, as the coefficients are left unchanged.


# Examples

```jldoctest
julia> f = Fun(x->x^2);

julia> domain(f) == ChebyshevInterval()
true

julia> g = setdomain(f, 0..1);

julia> domain(g) == 0..1
true

julia> coefficients(f) == coefficients(g)
true
```
