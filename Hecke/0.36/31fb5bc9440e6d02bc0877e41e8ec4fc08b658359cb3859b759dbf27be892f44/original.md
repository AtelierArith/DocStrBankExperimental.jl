```
lll_gram_indef_with_transform(G::MatElem{ZZRingElem}; check::Bool = false)
                                                    -> MatElem{ZZRingElem},
                                                       MatElem{ZZRingElem}
```

Given a full-rank symmetric matrix `G` with integer entries which defines the Gram matrix of an non-degenerate indefinite integral quadratic form `L`, compute an LLL-reduced basis `U` of `L` and return `(G', U)` where `G'` is the Gram matrix of `L` with respect to `U`.

Note: if `G` is not unimodular, eventually the algorithm has to be applied more than once.

# Examples

```jldoctest
julia> G = ZZ[0 1 2; 1 -1 3; 2 3 0];

julia> lll_gram_indef_with_transform(G)
([0 0 1; 0 -16 0; 1 0 1], [1 0 0; 5 2 -1; 1 1 0])

julia> G = ZZ[2 1 2 4;1 8 0 2;2 0 -2 5;4 2 5 0];

julia> lll_gram_indef_with_transform(G)
([2 0 1 0; 0 -4 -1 1; 1 -1 8 0; 0 1 0 -8], [1 0 0 0; -1 0 1 0; 0 1 0 0; -2 0 0 1])
```
