```
Translation{N, S<:LazySet{N}, VN<:AbstractVector{N}}
    <: AbstractAffineMap{N, S}
```

Type that represents a lazy translation.

The translation of set `X` along vector `v` is the map:

$$
x ↦ x + v,\qquad x ∈ X
$$

A translation is a special case of an affine map $A x + b, x ∈ X$ where the linear map $A$ is the identity matrix and the translation vector $b$ is $v$.

### Fields

  * `X` – set
  * `v` – vector that defines the translation

### Notes

Translation preserves convexity: if `X` is convex, then any translation of `X` is convex as well.

### Example

```jldoctest translation
julia> X = BallInf([2.0, 2.0, 2.0], 1.0);

julia> v = [1.0, 0.0, 0.0]; # translation along dimension 1

julia> tr = Translation(X, v);

julia> typeof(tr)
Translation{Float64, BallInf{Float64, Vector{Float64}}, Vector{Float64}}

julia> tr.X
BallInf{Float64, Vector{Float64}}([2.0, 2.0, 2.0], 1.0)

julia> tr.v
3-element Vector{Float64}:
 1.0
 0.0
 0.0
```

Both the sum operator `+` and the Minkowski-sum operator `⊕` are overloaded to create translations:

```jldoctest translation
julia> X + v == X ⊕ v == Translation(X, v)
true
```

The translation of a translation is performed immediately:

```jldoctest translation
julia> tr = (X + v) + v
Translation{Float64, BallInf{Float64, Vector{Float64}}, Vector{Float64}}(BallInf{Float64, Vector{Float64}}([2.0, 2.0, 2.0], 1.0), [2.0, 0.0, 0.0])

julia> tr.v
3-element Vector{Float64}:
 2.0
 0.0
 0.0
```

The dimension of a translation is obtained with the `dim` function:

```jldoctest translation
julia> dim(tr)
3
```

For the support vector (resp. support function) along vector `d`, use `σ` and `ρ`, respectively:

```jldoctest translation
julia> σ([1.0, 0.0, 0.0], tr)
3-element Vector{Float64}:
 5.0
 2.0
 2.0

julia> ρ([1.0, 0.0, 0.0], tr)
5.0
```

See the docstring of each of these functions for details.

The `an_element` function is useful to obtain an element of a translation:

```jldoctest translation
julia> e = an_element(tr)
3-element Vector{Float64}:
 4.0
 2.0
 2.0
```

The lazy linear map of a translation is an affine map, since the following simplification rule applies: $M * (X ⊕ v) = (M * X) ⊕ (M * v)$:

```jldoctest translation
julia> using LinearAlgebra: I

julia> M = Matrix(2.0I, 3, 3);

julia> Q = M * tr;

julia> Q isa AffineMap && Q.M == M && Q.X == tr.X && Q.v == 2 * tr.v
true
```

Use the `isempty` method to check whether the translation is empty:

```jldoctest translation
julia> isempty(tr)
false
```

The list of constraints of the translation of a polyhedral set (a set whose `constraints_list` is available) can be computed from a lazy translation:

```jldoctest translation
julia> constraints_list(tr)
6-element Vector{HalfSpace{Float64, ReachabilityBase.Arrays.SingleEntryVector{Float64}}}:
 HalfSpace{Float64, ReachabilityBase.Arrays.SingleEntryVector{Float64}}([1.0, 0.0, 0.0], 5.0)
 HalfSpace{Float64, ReachabilityBase.Arrays.SingleEntryVector{Float64}}([0.0, 1.0, 0.0], 3.0)
 HalfSpace{Float64, ReachabilityBase.Arrays.SingleEntryVector{Float64}}([0.0, 0.0, 1.0], 3.0)
 HalfSpace{Float64, ReachabilityBase.Arrays.SingleEntryVector{Float64}}([-1.0, 0.0, 0.0], -3.0)
 HalfSpace{Float64, ReachabilityBase.Arrays.SingleEntryVector{Float64}}([0.0, -1.0, 0.0], -1.0)
 HalfSpace{Float64, ReachabilityBase.Arrays.SingleEntryVector{Float64}}([0.0, 0.0, -1.0], -1.0)
```
