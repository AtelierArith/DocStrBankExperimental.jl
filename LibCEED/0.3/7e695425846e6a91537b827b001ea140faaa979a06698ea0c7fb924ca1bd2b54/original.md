```
create_interior_qfunction(ceed::Ceed, name::AbstractString)
```

Create a [`QFunction`](@ref) from the Q-function gallery, using the provided name.

# Examples

  * Build and apply the 3D mass operator

```
build_mass_qf = create_interior_qfunction(c, "Mass3DBuild")
apply_mass_qf = create_interior_qfunction(c, "MassApply")
```

  * Build and apply the 3D Poisson operator

```
build_poi_qf = create_interior_qfunction(c, "Poisson3DBuild")
apply_poi_qf = create_interior_qfunction(c, "Poisson3DApply")
```
