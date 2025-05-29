```
hrep(hyperplanes::HyperPlaneIt, halfspaces::HalfSpaceIt; d::FullDim)
```

Creates an H-representation for the polyhedron of full dimension `d` equal to the intersection of the hyperplanes `hyperplanes` and halfspaces `halfspaces`.

### Examples

For instance, the simplex

$$
\begin{aligned}
  x_1 + x_2 &= 1 \\
  x_1 &\geq 0 \\
  x_2 &\geq 0
\end{aligned}
$$

can be created as follows:

```jldoctest
julia> hrep([HyperPlane([1, 1], 1)], [HalfSpace([0, -1], 0), HalfSpace([-1, 0], 0)])
H-representation Polyhedra.Intersection{Int64, Vector{Int64}, Int64}:
1-element iterator of HyperPlane{Int64, Vector{Int64}}:
 HyperPlane([1, 1], 1),
2-element iterator of HalfSpace{Int64, Vector{Int64}}:
 HalfSpace([0, -1], 0)
 HalfSpace([-1, 0], 0)
```
