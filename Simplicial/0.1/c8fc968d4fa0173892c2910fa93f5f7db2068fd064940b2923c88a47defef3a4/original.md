```
SimplicialComplex{T}
```

Stores an abstract simplicial complex with vertices of type `T` by storing a list of its facets.

# Constructors

```
SimplicialComplex(itr, [vertices=union(itr...)])
```

Uses the maximal elements of `itr` as facets. Optional argument `vertices` can specify vertex set if some vertices do not appear as faces. The vertices are of type `eltype(vertices)`; if `vertices` is empty, the type `TheIntegerType` will be used. Note this constructor will sort the elements of `itr` according to [graded reverse lexicographic order](https://en.wikipedia.org/wiki/Monomial_order#Graded_reverse_lexicographic_order), see [`lessequal_GrRevLex`](@ref)

```
SimplicialComplex(B; order="rows")
```

Interprets rows of binary matrix `B` as codewords. If `order="cols"` first transposes `B`. Defaults to using `TheIntegerType` for vertices, but will use larger `Int` type as necessary (if `B` is *really* big).
