```julia
Mesh2D(dx, dy)
```

Two dimensional regular background mesh

# Arguments:

  * `dx::Float64`:  deformation in x dimension
  * `dy::Float64`:  deformation in y dimension

# Returns:

  * two dimensional mesh object

# Example:

```jldoctest
# generate 2D mesh
mesh = Mesh2D(1.0, 0.5);

# verify
println(mesh)

# output

2d mesh:
    dx: 1.0
    dy: 0.5
```
