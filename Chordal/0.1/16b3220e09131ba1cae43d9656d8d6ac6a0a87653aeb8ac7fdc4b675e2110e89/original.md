```
maxdet_completion(A::SparseMatrixCSC{Tv, Ti}) where {Tv <: AbstractFloat, Ti <: Integer}
```

Returns the maximum determinant completion of chordal sparse matrix `A` using Algorithm 10.2 in [VA15].

# Reference

[VA15] [Chordal Graphs and Semidefinite Optimization](https://www.seas.ucla.edu/~vandenbe/publications/chordalsdp.pdf) by Lieven Vandenberghe and Martin Andersen
