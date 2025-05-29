```
gens(A::AbstractAssociativeAlgebra; thorough_search::Bool = false) -> Vector
```

Given a $K$-algebra $A$, return a subset of `basis(A)`, which generates $A$ as an algebra over $K$.

If `thorough_search` is `true`, the number of returned generators is possibly smaller. This will in general increase the runtime. It is not guaranteed that the number of generators is minimal in any case.

The [`gens_with_data`](@ref) function computes additional data for expressing a basis as words in the generators.

# Examples

```jldoctest
julia> A = matrix_algebra(QQ, 3);

julia> gens(A; thorough_search = true)
5-element Vector{MatAlgebraElem{QQFieldElem, QQMatrix}}:
 [1 0 0; 0 0 0; 0 0 0]
 [0 0 0; 1 0 0; 0 0 0]
 [0 0 0; 0 0 0; 1 0 0]
 [0 1 0; 0 0 0; 0 0 0]
 [0 0 1; 0 0 0; 0 0 0]
```
