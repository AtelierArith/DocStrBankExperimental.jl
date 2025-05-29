```
defining_polynomial([R::FqPolyRing], K::FqField)
```

Return the defining polynomial of `K` as a polynomial over the base field of `K`.

If the polynomial ring `R` is specified, the polynomial will be an element of `R`.

# Examples

```jldoctest
julia> K, a = finite_field(9, "a");

julia> defining_polynomial(K)
x^2 + 2*x + 2

julia> Ky, y = K["y"];

julia> L, b = finite_field(y^3 + y^2 + y + 2, "b");

julia> defining_polynomial(L)
y^3 + y^2 + y + 2
```
