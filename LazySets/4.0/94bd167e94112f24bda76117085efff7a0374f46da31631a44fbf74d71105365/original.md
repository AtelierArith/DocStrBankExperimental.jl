```
project(P::AbstractPolyhedron, block::AbstractVector{Int}; [kwargs...])
```

Concrete projection of a polyhedral set.

### Input

  * `P`     – set
  * `block` – block structure, a vector with the dimensions of interest

### Output

A polyhedron representing the projection of `P` on the dimensions specified by `block`. If `P` was bounded, the result is an `HPolytope`; otherwise the result is an `HPolyhedron`. Note that there are more specific methods for specific input types, which give a different output type; e.g., projecting a `Ball1` results in a `Ball1`.

### Algorithm

  * We first try to exploit the special case where each of the constraints of `P` and `block` are *compatible*, which is one of the two cases described below. Let `c` be a constraint of `P` and let $D_c$ and $D_b$ be the set of dimensions in which `c` resp. `block` are constrained.

      * If $D_c ⊆ D_b$, then one can project the normal vector of `c`.
      * If $D_c ∩ D_b = ∅$, then the constraint becomes redundant.
  * In the general case, we compute the concrete linear map of the projection matrix associated to the given block structure.

### Examples

Consider the four-dimensional cross-polytope (unit ball in the 1-norm):

```jldoctest project_polyhedron
julia> P = convert(HPolytope, Ball1(zeros(4), 1.0));
```

All dimensions are constrained, and computing the (trivial) projection on the whole space behaves as expected:

```jldoctest project_polyhedron
julia> constrained_dimensions(P)
4-element Vector{Int64}:
 1
 2
 3
 4

julia> project(P, [1, 2, 3, 4]) == P
true
```

Each constraint of the cross polytope is constrained in all dimensions.

Now let us take a ball in the infinity norm and remove some constraints:

```jldoctest project_polyhedron
julia> B = BallInf(zeros(4), 1.0);

julia> c = constraints_list(B)[1:2]
2-element Vector{HalfSpace{Float64, ReachabilityBase.Arrays.SingleEntryVector{Float64}}}:
 HalfSpace{Float64, ReachabilityBase.Arrays.SingleEntryVector{Float64}}([1.0, 0.0, 0.0, 0.0], 1.0)
 HalfSpace{Float64, ReachabilityBase.Arrays.SingleEntryVector{Float64}}([0.0, 1.0, 0.0, 0.0], 1.0)

julia> P = HPolyhedron(c);

julia> constrained_dimensions(P)
2-element Vector{Int64}:
 1
 2
```

Finally, we take the concrete projection onto variables `1` and `2`:

```jldoctest project_polyhedron
julia> project(P, [1, 2]) |> constraints_list
2-element Vector{HalfSpace{Float64, Vector{Float64}}}:
 HalfSpace{Float64, Vector{Float64}}([1.0, 0.0], 1.0)
 HalfSpace{Float64, Vector{Float64}}([0.0, 1.0], 1.0)
```
