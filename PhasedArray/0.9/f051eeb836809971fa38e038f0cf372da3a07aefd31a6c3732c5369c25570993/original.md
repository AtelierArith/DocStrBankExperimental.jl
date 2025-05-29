Calculates the manifold based on antenna position and signal frequency.

# Examples

```julia-repl
julia> manifold = IdealManifold(1575420e3, 0.1904 / 4 * SVector(SVector(1, 1, 0), SVector(-1, 1, 0), SVector(1, -1, 0), SVector(-1, -1, 0)))
julia> get_steer_vec(manifold, SVector(0.0,0.0,1.0))
julia> get_steer_vec(manifold, SVector(0.0,0.0,1.0), RotXYZ(0.0,0.0,0.0))
```
