```
ExponentialProjectionMap{N, S<:LazySet{N}} <: AbstractAffineMap{N, S}
```

Type that represents the application of a projection of a sparse matrix exponential to a set.

### Fields

  * `spmexp` – projection of a sparse matrix exponential
  * `X`      – set

### Notes

The exponential projection preserves convexity: if `X` is convex, then any exponential projection of `X` is convex as well.

### Examples

We use a random sparse projection matrix of dimensions $6 × 6$ with occupation probability $0.5$ and apply it to the 2D unit ball in the infinity norm:

```jldoctest
julia> using SparseArrays

julia> R = sparse([5, 6], [1, 2], [1.0, 1.0]);

julia> L = sparse([1, 2], [1, 2], [1.0, 1.0], 2, 6);

julia> using ExponentialUtilities

julia> A = sprandn(6, 6, 0.5);

julia> E = SparseMatrixExp(A);

julia> M = ProjectionSparseMatrixExp(L, E, R);

julia> B = BallInf(zeros(2), 1.0);

julia> X = ExponentialProjectionMap(M, B);

julia> dim(X)
2
```
