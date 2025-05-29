```
rotatey!(m::Mesh, θ)
```

Rotate a mesh `m` around the y axis by angle `θ`.

# Arguments

  * `m`: The mesh to be scaled.
  * `θ`: Angle of rotation in radians.

# Examples

```jldoctest
julia> m = Rectangle();

julia> θ = pi/2;

julia> rotatey!(m, θ);
```
