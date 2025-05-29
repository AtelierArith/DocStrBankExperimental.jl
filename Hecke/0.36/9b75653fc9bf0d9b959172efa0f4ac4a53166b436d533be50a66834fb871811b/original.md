```
infinite_place(e::NumFieldEmb)
```

Construct the infinite place induced by the given complex embedding.

```jldoctest
julia> K,  = quadratic_field(5);

julia> infinite_place(complex_embedding(K, 2.24))
Infinite place
  of real quadratic field defined by x^2 - 5
corresponding to
  real embedding with 2.24 of K
```
