```
gens_with_data(A::AbstractAssociativeAlgebra; thorough_search::Bool = false)
                                                   -> Vector, Vector, Vector
```

Given a $K$-algebra $A$, return a triple $(G, B, w)$ consisting of

  * a subset $G$ of `basis(A)`, which generates $A$ as an algebra over $K$,
  * a (new) basis $B$ and a vector `w::Vector{Tuple{Int, Int}}`, such that `B[i] = prod(G[j]^k for (j, k) in w[i]`.

If `thorough_search` is `true`, the number of returned generators is possibly smaller. This will in general increase the runtime. It is not guaranteed that the number of generators is minimal in any case.

# Examples

```jldoctest
julia> A = matrix_algebra(QQ, 3);

julia> G, B, w = gens_with_data(A; thorough_search = true);

julia> B[1] == prod(G[i]^j for (i, j) in w[1])
true
```
