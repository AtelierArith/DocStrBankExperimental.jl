```julia
Mesh3D(dx, dy, dz)
```

Three dimensional regular background mesh

# Arguments:

  * `dx::Float64`:  deformation in x dimension
  * `dy::Float64`:  deformation in y dimension
  * `dz::Float64`:  deformation in z dimension

# Returns:

  * three dimensional mesh object

# Example:

```jldoctest
# generate 3D mesh
mesh = Mesh3D(1.0, 0.5, 0.3);

# verify
println(mesh)

# output

3d mesh:
    dx: 1.0
    dy: 0.5
    dz: 0.3
```
