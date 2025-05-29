```
restrict(p::InfPlc, K::NumField)
```

Given an infinite place `p` of a number field `L` and a number field `K` appearing as a base field of `L`, return the restriction of `p` to `L`.

# Examples

```jldoctest
julia> K, a = quadratic_field(3);

julia> L, b = number_field(polynomial(K, [1, 0, 1]), "b");

julia> p = complex_places(L)[1];

julia> restrict(p, K)
Infinite place of
Real quadratic field defined by x^2 - 3
corresponding to
Complex embedding corresponding to -1.73 of K
```
