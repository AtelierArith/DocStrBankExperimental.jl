```
lll_gram_indef_isotropic(G::MatElem{ZZRingElem}, base::Bool = false)
                                                    -> MatElem{ZZRingElem},
                                                       MatElem{ZZRingElem},
                                                       MatElem{ZZRingElem}}
```

Given a full-rank symmetric matrix `G` with integer entries which defines the Gram matrix of an indefinite integral quadratic form `L`, return `G`, `I` and `sol` where `I` is the identity matrix and `sol` is an isotropic vector of `L`, if such a vector is found.

If no isotropic vector of `L` is found, compute an LLL-reduced basis `U` of `L` and return `G`, the LLL-reduced basis matrix `U` and the empty vector `ZZRingElem[]`.

If `base` is set to `true`, the first output is replaced by `U*G*transpose(U)`, the Gram matrix of `L` with respect to `U`.

# Examples

```jldoctest
julia> G = ZZ[0 1 2; 1 -1 3; 2 3 0];

julia> lll_gram_indef_isotropic(G)
([0 1 2; 1 -1 3; 2 3 0], [1 0 0; 0 1 0; 0 0 1], [1 0 0])

julia> (ans[3]*G*transpose(ans[3]))[1] == 0
true

julia> G = ZZ[2 1 2 4;1 8 0 2;2 0 -2 5;4 2 5 0];

julia> lll_gram_indef_isotropic(G)
([2 0 1 0; 0 -4 -1 1; 1 -1 8 0; 0 1 0 -8], [1 0 0 0; -1 0 1 0; 0 1 0 0; -2 0 0 1], ZZRingElem[])
```
