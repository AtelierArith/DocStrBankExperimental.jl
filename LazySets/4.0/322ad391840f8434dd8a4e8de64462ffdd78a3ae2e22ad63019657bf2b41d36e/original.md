```
vertices_list(P::AbstractPolyhedron; check_boundedness::Bool=true)
```

Return the list of vertices of a polyhedron in constraint representation.

### Input

  * `P`                 – polyhedron in constraint representation
  * `check_boundedness` – (optional, default: `true`) if `true`, check whether                        the polyhedron is bounded

### Output

The list of vertices of `P`, or an error if `P` is unbounded.

### Notes

This function throws an error if the polyhedron is unbounded. Otherwise, the polyhedron is converted to an `HPolytope` and its list of vertices is computed.

### Examples

```jldoctest
julia> P = HPolyhedron([HalfSpace([1.0, 0.0], 1.0),
                        HalfSpace([0.0, 1.0], 1.0),
                        HalfSpace([-1.0, 0.0], 1.0),
                        HalfSpace([0.0, -1.0], 1.0)]);

julia> length(vertices_list(P))
4
```
