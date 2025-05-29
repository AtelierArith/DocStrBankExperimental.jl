```
InverseLinearMap{N, S<:LazySet{N}, NM, MAT<:AbstractMatrix{NM}}
    <: AbstractAffineMap{N, S}
```

Given a linear transformation $M$, this type represents the linear transformation $M⁻¹⋅X$ of a set $X$ without actually computing $M⁻¹$.

### Fields

  * `M` – matrix (typically invertible, which can be checked in the constructor)
  * `X` – set

### Notes

Many set operations avoid computing the inverse of the matrix.

In principle, the matrix does not have to be invertible (it can for instance be rectangular) for many set operations.

This type is parametric in the elements of the inverse linear map, `NM`, which is independent of the numeric type of the wrapped set (`N`). Typically `NM = N`, but there may be exceptions, e.g., if `NM` is an interval that holds numbers of type `N`, where `N` is a floating-point type such as `Float64`.

### Examples

For the examples we create a $3×3$ matrix and a unit three-dimensional square.

```jldoctest ilp_constructor
julia> A = [1 2 3; 2 3 1; 3 1 2];

julia> X = BallInf([0, 0, 0], 1);

julia> ilm = InverseLinearMap(A, X)
InverseLinearMap{Int64, BallInf{Int64, Vector{Int64}}, Int64, Matrix{Int64}}([1 2 3; 2 3 1; 3 1 2], BallInf{Int64, Vector{Int64}}([0, 0, 0], 1))
```

Applying an inverse linear map to a `InverseLinearMap` object combines the two maps into a single `InverseLinearMap` instance.

```jldoctest ilp_constructor
julia> B = transpose(A); ilm2 = InverseLinearMap(B, ilm)
InverseLinearMap{Int64, BallInf{Int64, Vector{Int64}}, Int64, Matrix{Int64}}([14 11 11; 11 14 11; 11 11 14], BallInf{Int64, Vector{Int64}}([0, 0, 0], 1))

julia> ilm2.M == A*B
true
```

The application of an `InverseLinearMap` to a `ZeroSet` or an `EmptySet` is simplified automatically.

```jldoctest ilp_constructor
julia> InverseLinearMap(A, ZeroSet{Int}(3))
ZeroSet{Int64}(3)
```
