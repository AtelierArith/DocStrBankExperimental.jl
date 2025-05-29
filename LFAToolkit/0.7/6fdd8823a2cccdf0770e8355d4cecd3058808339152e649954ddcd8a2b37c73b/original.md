```julia
Mesh1D(dx)
```

One dimensional regular background mesh

# Arguments:

  * `dx::Float64`:  deformation in x dimension

# Returns:

  * one dimensional mesh object

# Example:

```jldoctest
# generate 1D mesh
mesh = Mesh1D(1.0);

# verify
println(mesh)

# output

1d mesh:
    dx: 1.0
```
