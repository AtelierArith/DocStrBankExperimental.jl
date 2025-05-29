```
AffineMap{N, S<:LazySet{N}, NM, MAT<:AbstractMatrix{NM},
          VN<:AbstractVector{NM}} <: AbstractAffineMap{N, S}
```

Type that represents an affine transformation $M⋅X ⊕ v$ of a set $X$, i.e., the set

$$
Y = \{ y ∈ ℝ^n : y = Mx + v,\qquad x ∈ X \}.
$$

If $X$ is $n$-dimensional, then $M$ should be an $m × n$ matrix and $v$ should be an $m$-dimensional vector.

### Fields

  * `M` – matrix
  * `X` – set
  * `v` – translation vector

The fields' getter functions are `matrix`, `set` and `vector`, respectively.

### Notes

An affine map is the composition of a linear map and a translation. This type is parametric in the coefficients of the linear map, `NM`, which may be different from the numeric type of the wrapped set, `N`. However, the numeric type of the translation vector should be `NM`.

An affine map preserves convexity: if `X` is convex, then any affine map of `X` is convex as well.

### Examples

For the examples we create a $3×2$ matrix, a two-dimensional unit square, and a three-dimensional vector. Then we combine them in an `AffineMap`.

```jldoctest constructors
julia> A = [1 2; 1 3; 1 4]; X = BallInf([0, 0], 1); b2 = [1, 2]; b3 = [1, 2, 3];

julia> AffineMap(A, X, b3)
AffineMap{Int64, BallInf{Int64, Vector{Int64}}, Int64, Matrix{Int64}, Vector{Int64}}([1 2; 1 3; 1 4], BallInf{Int64, Vector{Int64}}([0, 0], 1), [1, 2, 3])
```

For convenience, `A` does not need to be a matrix; we also allow to use `UniformScaling`s resp. scalars (interpreted as a scaling, i.e., a scaled identity matrix). Scaling by $1$ is ignored and simplified to a pure `Translation`.

```jldoctest constructors
julia> using LinearAlgebra

julia> am = AffineMap(2I, X, b2)
AffineMap{Int64, BallInf{Int64, Vector{Int64}}, Int64, Diagonal{Int64, Vector{Int64}}, Vector{Int64}}([2 0; 0 2], BallInf{Int64, Vector{Int64}}([0, 0], 1), [1, 2])

julia> AffineMap(2, X, b2) == am
true

julia> AffineMap(1, X, b2)
Translation{Int64, BallInf{Int64, Vector{Int64}}, Vector{Int64}}(BallInf{Int64, Vector{Int64}}([0, 0], 1), [1, 2])
```

Applying a linear map to an `AffineMap` object combines the two maps into a new `AffineMap` instance. Again we can make use of the conversion for convenience.

```jldoctest constructors
julia> B = [2 0; 0 2]; am2 = B * am
AffineMap{Int64, BallInf{Int64, Vector{Int64}}, Int64, Matrix{Int64}, Vector{Int64}}([4 0; 0 4], BallInf{Int64, Vector{Int64}}([0, 0], 1), [2, 4])

julia> 2 * am == am2
true
```

The application of an `AffineMap` to a `ZeroSet` or an `EmptySet` is simplified automatically.

```jldoctest constructors
julia> AffineMap(A, ZeroSet{Int}(2), b3)
Singleton{Int64, Vector{Int64}}([1, 2, 3])

julia> AffineMap(A, EmptySet{Int}(2), b3)
EmptySet{Int64}(2)
```
