```
closest_points(p, q, dir; max_iter=100, atol=0.0)
```

Compute the closest points between convex objects `p` and `q` if they are not colliding within some tolerance. Provide an initial search direction `dir` in the space of the problem.

Return result of type Tuple with StaticArrays of the two closest points on each object.

# Examples

```julia-repl
julia> using StaticArrays
julia> p = SMatrix{2,3}([0.0 0.0 1.0; 0.0 2.0 1.0])
julia> q = SMatrix{2,3}([2.0 2.0 3.0; 0.0 2.0 1.0])
julia> dir = SVector{2}(1.0, 0.0)
julia> closest_points(p, q, dir)
([1.0, 1.0], [2.0, 1.0])
```
