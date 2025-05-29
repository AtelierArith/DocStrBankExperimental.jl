```
ExponentialMap{N, S<:LazySet{N}} <: AbstractAffineMap{N, S}
```

Type that represents the action of an exponential map on a set.

### Fields

  * `spmexp` – sparse matrix exponential
  * `X`      – set

### Notes

The exponential map preserves convexity: if `X` is convex, then any exponential map of `X` is convex as well.

### Examples

The `ExponentialMap` type is overloaded to the usual times (`*`) operator when the linear map is a lazy matrix exponential. For instance:

```jldoctest constructors
julia> using SparseArrays

julia> A = sprandn(100, 100, 0.1);

julia> E = SparseMatrixExp(A);

julia> B = BallInf(zeros(100), 1.);

julia> M = E * B;  # represents the set: exp(A) * B

julia> M isa ExponentialMap
true

julia> dim(M)
100
```

The application of an `ExponentialMap` to a `ZeroSet` or an `EmptySet` is simplified automatically.

```jldoctest constructors
julia> E * ZeroSet(100)
ZeroSet{Float64}(100)

julia> E * EmptySet(100)
∅(100)
```
