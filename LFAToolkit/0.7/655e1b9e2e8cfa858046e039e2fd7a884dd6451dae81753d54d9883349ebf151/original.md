```julia
IdentityPC()
```

Identity preconditioner to investigate multigrid without smoother

# Returns:

  * identity preconditioner object

# Example:

```jldoctest
# setup
mesh = Mesh2D(1.0, 1.0);
mass = GalleryOperator("mass", 4, 4, mesh);

# preconditioner
identity = IdentityPC(mass);

# verify
println(identity)

# output

identity preconditioner
```
