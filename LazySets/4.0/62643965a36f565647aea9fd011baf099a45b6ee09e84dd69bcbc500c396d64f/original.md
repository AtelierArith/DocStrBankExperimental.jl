```
LinearMap{N, S<:LazySet{N}, NM, MAT<:AbstractMatrix{NM}}
    <: AbstractAffineMap{N, S}
```

Type that represents a linear transformation $M⋅X$ of a set $X$.

### Fields

  * `M` – matrix/linear map
  * `X` – set

### Notes

This type is parametric in the elements of the linear map, `NM`, which is independent of the numeric type of the wrapped set (`N`). Typically `NM = N`, but there may be exceptions, e.g., if `NM` is an interval that holds numbers of type `N`, where `N` is a floating point number type such as `Float64`.

The linear map preserves convexity: if `X` is convex, then any linear map of `X` is convex as well.

### Examples

For the examples we create a $3×2$ matrix and a two-dimensional unit square.

```jldoctest constructors
julia> M = [1 2; 1 3; 1 4]; X = BallInf([0, 0], 1);
```

The function $*$ can be used as an alias to construct a `LinearMap` object.

```jldoctest constructors
julia> lm = LinearMap(M, X)
LinearMap{Int64, BallInf{Int64, Vector{Int64}}, Int64, Matrix{Int64}}([1 2; 1 3; 1 4], BallInf{Int64, Vector{Int64}}([0, 0], 1))

julia> lm2 = M * X
LinearMap{Int64, BallInf{Int64, Vector{Int64}}, Int64, Matrix{Int64}}([1 2; 1 3; 1 4], BallInf{Int64, Vector{Int64}}([0, 0], 1))

julia> lm == lm2
true
```

For convenience, `M` does not need to be a matrix; we also allow to use vectors (interpreted as an $n×1$ matrix) and `UniformScaling`s resp. scalars (interpreted as a scaling, i.e., a scaled identity matrix). Scaling by $1$ is ignored.

```jldoctest constructors
julia> using LinearAlgebra: I

julia> Y = BallInf([0], 1);  # one-dimensional interval

julia> [2, 3] * Y
LinearMap{Int64, BallInf{Int64, Vector{Int64}}, Int64, Matrix{Int64}}([2; 3;;], BallInf{Int64, Vector{Int64}}([0], 1))

julia> lm3 = 2 * X
LinearMap{Int64, BallInf{Int64, Vector{Int64}}, Int64, SparseArrays.SparseMatrixCSC{Int64, Int64}}(sparse([1, 2], [1, 2], [2, 2], 2, 2), BallInf{Int64, Vector{Int64}}([0, 0], 1))

julia> 2I * X == lm3
true

julia> 1I * X == X
true
```

Applying a linear map to a `LinearMap` object combines the two maps into a single `LinearMap` instance. Again we can make use of the conversion for convenience.

```jldoctest constructors
julia> B = transpose(M); B * lm
LinearMap{Int64, BallInf{Int64, Vector{Int64}}, Int64, Matrix{Int64}}([3 9; 9 29], BallInf{Int64, Vector{Int64}}([0, 0], 1))

julia> B = [3, 4, 5]; B * lm
LinearMap{Int64, BallInf{Int64, Vector{Int64}}, Int64, Matrix{Int64}}([12 38], BallInf{Int64, Vector{Int64}}([0, 0], 1))

julia> B = 2; B * lm
LinearMap{Int64, BallInf{Int64, Vector{Int64}}, Int64, Matrix{Int64}}([2 4; 2 6; 2 8], BallInf{Int64, Vector{Int64}}([0, 0], 1))
```

The application of a `LinearMap` to a `ZeroSet` or an `EmptySet` is simplified automatically.

```jldoctest constructors
julia> M * ZeroSet{Int}(2)
ZeroSet{Int64}(3)

julia> M * EmptySet{Int}(2)
EmptySet{Int64}(3)
```
