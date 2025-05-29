```
tolerance_verification(p, q, dir, τ; max_iter=100, atol=0.0)
```

Compute if the convex objects `p` and `q` are at least `τ` tolerance apart within some tolerance. Provide an initial search direction `dir` in the space of the problem.

# Examples

```julia-repl
julia> using StaticArrays
julia> p = SMatrix{2,3}([0.0 0.0 1.0; 0.0 2.0 1.0])
julia> q = SMatrix{2,3}([2.0 2.0 3.0; 0.0 2.0 1.0])
julia> dir = SVector{2}(1.0, 0.0)
julia> tolerance_verification(p, q, dir, 0.25)
true
```
