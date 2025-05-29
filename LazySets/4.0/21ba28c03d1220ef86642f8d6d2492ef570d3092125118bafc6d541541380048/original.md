```
vertices_list(P::AbstractHPolygon;
              apply_convex_hull::Bool=true,
              check_feasibility::Bool=true)
```

Return the list of vertices of a polygon in constraint representation.

### Input

  * `P`                 – polygon in constraint representation
  * `apply_convex_hull` – (optional, default: `true`) flag to post-process the                        intersection of constraints with a convex hull
  * `check_feasibility` – (optional, default: `true`) flag to check whether the                        polygon was empty (required for correctness in case of                        empty polygons)

### Output

List of vertices.

### Notes

By construction an `AbstractHPolygon` should not contain any redundant vertices. Still the `apply_convex_hull` argument is activated by default to remove potential duplicate vertices. They can exist due to numeric instability.

```jldoctest
julia> p = HPolygon([HalfSpace([1.0, 0.0], 1.0),
                     HalfSpace([0.0, 1.0], 1.0),
                     HalfSpace([-1.0, 0.0], -1.0),
                     HalfSpace([0.0, -1.0], -1.0)]);

julia> vertices_list(p, apply_convex_hull=false)
4-element Vector{Vector{Float64}}:
 [1.0, 1.0]
 [1.0, 1.0]
 [1.0, 1.0]
 [1.0, 1.0]
```

If it is known that each constraint has a "proper" distance to the next vertex, this step can be skipped.

### Algorithm

We compute each vertex as the intersection of consecutive lines defined by the half-spaces. If `check_feasibility` is active, we then check if the constraints of the polygon were actually feasible (i.e., they pointed in the *right* direction). For this we compute the *average* of all vertices and check membership in each constraint.
