A lower triangular array implementation that only stores the non-zero entries explicitly. `L<:AbstractArray{T,N-1}` although we do allow both "flat" `N-1`-dimensional indexing and  additional `N`-dimensional or "matrix-style" indexing.

Supports n-dimensional lower triangular arrays, so that for all trailing dimensions `L[:, :, ..]` is a matrix in lower triangular form, e.g. a (5x5x3)-LowerTriangularArray would hold 3 lower triangular matrices.
