```
structure_constant_algebra(R::Ring, sctable::Array{_, 3}; one::Vector = nothing,
                                                          check::Bool = true)
```

Given an array with dimensions $(d, d, d)$ and a ring $R$, return the $d$-dimensional structure constant algebra over $R$. The basis `e` of $R$ satisfies `e[i] * e[j] = sum(sctable[i,j,k] * e[k] for k in 1:d)`.

Unless `check = false`, this includes (time consuming) associativity and distributivity checks.  If `one` is given, record the element with the supplied coordinate vector as the one element of the algebra.

# Examples

```jldoctest
julia> associative_algebra(QQ, reshape([1, 0, 0, 2, 0, 1, 1, 0], (2, 2, 2)))
Structure constant algebra of dimension 2 over QQ
```
