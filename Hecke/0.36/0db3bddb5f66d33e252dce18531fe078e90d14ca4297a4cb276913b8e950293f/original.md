```
restrict(f::NumFieldEmb, K::NumField)
```

Given an embedding $f$ of a number field $L$ and a number field $K$ appearing as a base field of $L$, return the restriction of $f$ to $K$.

# Examples

```jldoctest
julia> K, a = quadratic_field(3);

julia> L, b = number_field(polynomial(K, [1, 0, 1]), "b");

julia> e = complex_embeddings(L);

julia> restrict(e[1], K)
Real embedding
  of real quadratic field defined by x^2 - 3
corresponding to root -1.73
```
