```
CombinatorialCode{T<:Integer}
```

A collection of subsets of $[n] = {1,...,n}$. Codewords are stored as `Set{T}` objects in an array.

# Constructors

```
CombinatorialCode(itr, [vertices=union(itr...)])
```

Collects the unique elements of iterable collection `itr` as codewords. Optional argument `vertices` allows creation of trivial neurons, i.e. neurons which never fire. The vertices are of type `eltype(vertices)`; if `vertices` is empty, the type `TheIntegerType` will be used. Words are stored in graded reverse lexicographic order by their binary vector representation  (see [`lessequal_GrRevLex`](@ref)).

```
CombinatorialCode(B::AbstractMatrix{Bool}; order="rows")
```

Interprets rows of matrix `B` as codewords. Keyword argument `order` is either `"rows"` or `"cols"` to specify whether rows of `B` or columns of `B` should be interpreted as codewords. Defaults to using `TheIntegerType` for vertices unless `B` is *very* large, in which case smalles useable integer type is used.
