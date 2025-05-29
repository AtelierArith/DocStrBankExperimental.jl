```
edm_completion(A::SparseMatrixCSC{Tv, Ti}) where {Tv <: AbstractFloat, Ti <: Integer}
```

Returns a Euclidean distance matrix completion of `A` if it is EDM-completable using Algorithm 11.1 in [VA15].

# Reference

[VA15] [Chordal Graphs and Semidefinite Optimization](https://www.seas.ucla.edu/~vandenbe/publications/chordalsdp.pdf) by Lieven Vandenberghe and Martin Andersen
