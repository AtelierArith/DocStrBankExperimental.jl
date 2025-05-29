```
degree(K::FqField) -> Int
```

Return the degree of the given finite field over the base field.

# Examples

```jldoctest
julia> K, a = finite_field(3, 2, "a");

julia> degree(K)
2

julia> Kx, x = K["x"];

julia> L, b = finite_field(x^3 + x^2 + x + 2, "b");

julia> degree(L)
3
```
