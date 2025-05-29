```
FDMesh(; dx=1e-9, dy=1e-9, dz=1e-9, nx=1, ny=1, nz=1, pbc="open")
```

Create a finite difference mesh (`FDMesh`) for simulations. This method is designed for the [Micromagnetic model](@ref).

This constructor initializes a finite difference mesh with the specified parameters. The `pbc` (periodic boundary conditions) parameter can be any combination of the characters `"x"`, `"y"`, and `"z"`, which determines whether the mesh wraps around the corresponding axis.

**Parameters:**

  * `dx::Float64`: Grid spacing in the x-direction (default: `1e-9`).
  * `dy::Float64`: Grid spacing in the y-direction (default: `1e-9`).
  * `dz::Float64`: Grid spacing in the z-direction (default: `1e-9`).
  * `nx::Int`: Number of grid points in the x-direction (default: `1`).
  * `ny::Int`: Number of grid points in the y-direction (default: `1`).
  * `nz::Int`: Number of grid points in the z-direction (default: `1`).
  * `pbc::String`: Periodic boundary conditions, which could be any combination of `"x"`, `"y"`, and `"z"` (default: `"open"`).

**Examples:**

```julia
mesh = FDMesh(dx=1e-8, dy=1e-8, dz=1e-8, nx=10, ny=10, nz=10, pbc="xyz")
```

This creates a FDMesh with 10 grid points in each direction and periodic boundary conditions in all three axes. 
