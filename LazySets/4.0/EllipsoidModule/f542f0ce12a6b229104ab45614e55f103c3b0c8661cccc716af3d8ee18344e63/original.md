```
Ellipsoid{N<:AbstractFloat, VN<:AbstractVector{N},
          MN<:AbstractMatrix{N}} <: AbstractCentrallySymmetric{N}
```

Type that represents an ellipsoid.

It is defined as the set

$$
E = \left\{ x ∈ ℝ^n : (x-c)^T Q^{-1} (x-c) ≤ 1 \right\},
$$

where $c ∈ ℝ^n$ is its *center* and $Q ∈ ℝ^{n×n}$ its *shape matrix*, which should be a positive definite matrix. An ellipsoid can also be characterized as the image of a Euclidean ball by an invertible linear transformation. It is the higher-dimensional generalization of an ellipse.

### Fields

  * `center`       – center of the ellipsoid
  * `shape_matrix` – real positive definite matrix, i.e., it is equal to its                   transpose and $x^\mathrm{T}Qx > 0$ for all nonzero $x$

## Notes

By default, the inner constructor checks that the given shape matrix is positive definite. Use the flag `check_posdef=false` to disable this check.

### Examples

We create a two-dimensional ellipsoid with center `[1, 1]`:

```jldoctest ellipsoid_constructor
julia> using LinearAlgebra

julia> E = Ellipsoid(ones(2), Diagonal([2.0, 0.5]))
Ellipsoid{Float64, Vector{Float64}, Diagonal{Float64, Vector{Float64}}}([1.0, 1.0], [2.0 0.0; 0.0 0.5])
```

If the center is not specified, it is assumed that it is the origin. For instance, a three-dimensional ellipsoid centered in the origin with the shape matrix being the identity can be created as follows:

```jldoctest ellipsoid_constructor
julia> E = Ellipsoid(Matrix(1.0I, 3, 3))
Ellipsoid{Float64, Vector{Float64}, Matrix{Float64}}([0.0, 0.0, 0.0], [1.0 0.0 0.0; 0.0 1.0 0.0; 0.0 0.0 1.0])

julia> dim(E)
3
```

The center and shape matrix of the ellipsoid can be retrieved with the functions `center` and `shape_matrix`, respectively:

```jldoctest ellipsoid_constructor
julia> center(E)
3-element Vector{Float64}:
 0.0
 0.0
 0.0

julia> shape_matrix(E)
3×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0
```

The function `an_element` returns some element of the ellipsoid:

```jldoctest ellipsoid_constructor
julia> an_element(E)
3-element Vector{Float64}:
 0.0
 0.0
 0.0

julia> an_element(E) ∈ E
true
```

We can evaluate the support vector in a given direction, say `[1, 1, 1]`:

```jldoctest ellipsoid_constructor
julia> σ(ones(3), E)
3-element Vector{Float64}:
 0.5773502691896258
 0.5773502691896258
 0.5773502691896258
```
