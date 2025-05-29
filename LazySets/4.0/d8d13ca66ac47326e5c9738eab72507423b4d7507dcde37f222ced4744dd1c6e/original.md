```
ResetMap{N, S<:LazySet{N}} <: AbstractAffineMap{N, S}
```

Type that represents a lazy reset map. A reset map is a special case of an affine map $A x + b, x ∈ X$ where the linear map $A$ is the identity matrix with zero entries in all reset dimensions, and the translation vector $b$ is zero in all other dimensions.

### Fields

  * `X`      – set
  * `resets` – resets (a mapping from an index to a new value)

### Notes

The reset map preserves convexity: if `X` is convex, then any reset map of `X` is convex as well.

### Examples

```jldoctest resetmap
julia> X = BallInf([2.0, 2.0, 2.0], 1.0);

julia> r = Dict(1 => 4.0, 3 => 0.0);

julia> rm = ResetMap(X, r);

```

Here `rm` modifies the set `X` such that `x1` is reset to 4 and `x3` is reset to 0, while `x2` is not modified. Hence `rm` is equivalent to the set `VPolytope([[4.0, 1.0, 0.0], [4.0, 3.0, 0.0]])`, i.e., an axis-aligned line segment embedded in 3D.

The corresponding affine map $A x + b$ would be:

$$
    egin{pmatrix} 0 & 0 & 0 \ 0 & 1 & 0 \ 0 & 0 & 0 nd{pmatrix} x +
    egin{pmatrix} 4 & 0 & 0 nd{pmatrix}
$$

Use the function `matrix` (resp. `vector`) to create the matrix `A` (resp. vector `b`) corresponding to a given reset map.

```jldoctest resetmap
julia> matrix(rm)
3×3 LinearAlgebra.Diagonal{Float64, Vector{Float64}}:
 0.0   ⋅    ⋅
  ⋅   1.0   ⋅
  ⋅    ⋅   0.0

julia> vector(rm)
3-element SparseArrays.SparseVector{Float64, Int64} with 1 stored entry:
  [1]  =  4.0
```

The application of a `ResetMap` to a `ZeroSet` or an `EmptySet` is simplified automatically.

```jldoctest resetmap
julia> ResetMap(ZeroSet(3), r)
Singleton{Float64, SparseArrays.SparseVector{Float64, Int64}}(sparsevec([1], [4.0], 3))

julia> ResetMap(EmptySet(3), r)
∅(3)
```

The (in this case unique) support vector of `rm` in direction `[1, 1, 1]` is:

```jldoctest resetmap
julia> σ(ones(3), rm)
3-element Vector{Float64}:
 4.0
 3.0
 0.0
```
