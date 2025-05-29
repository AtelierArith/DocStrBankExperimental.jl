```
lll_gram_indef_ternary_hyperbolic(G::MatElem{ZZRingElem}; check::Bool = false)
                                                    -> MatElem{ZZRingElem},
                                                       MatElem{ZZRingElem}
```

Given a full-rank symmetric matrix `G` with integer entries which defines the Gram matrix of a non-degenerate ternary hyperbolic integral quadratic form `L`, compute an LLL-reduced basis `U` of `L` and return `(G', U)` where `G'` is the Gram matrix of `L` with respect to `U`.

# Examples

```jldoctest
julia> G = ZZ[1 0 0; 0 4 3; 0 3 2];

julia> lll_gram_indef_ternary_hyperbolic(G)
([0 0 -1; 0 1 0; -1 0 0], [-1 -1 0; 0 0 -1; -2 -1 0])
```
