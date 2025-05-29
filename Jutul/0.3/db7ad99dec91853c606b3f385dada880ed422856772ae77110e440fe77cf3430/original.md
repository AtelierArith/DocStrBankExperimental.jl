```
CartesianMesh(dims, [Δ, [origin]])
```

Create a Cartesian mesh with dimensions specified by the `Tuple` `dims`.

# Arguments

  * `dims::Tuple`: Number of grid cells in each direction. For example, `(nx, ny)` will give a 2D grids with `nx` cells in the x-direction.
  * `Δ::Tuple=Tuple(ones(length(dims)))`: Equal length to `dims`. First option: A

`Tuple` of scalars where each entry is the length of each cell in that direction. For example, specifying `(Δx, Δy) for a uniform grid with each grid cell having area of`Δx*Δy`. Second option: A`Tuple` of vectors where each entry contains the cell sizes in the direction.

  * `origin=zeros(length(dims))`: The origin of the first corner in the grid.

# Examples

Generate a uniform 3D mesh that discretizes a domain of 2 by 3 by 5 units with 3 by 5 by 2 cells:

```julia-repl
julia> CartesianMesh((3, 5, 2), (2.0, 3.0, 5.0))
CartesianMesh (3D) with 3x5x2=30 cells
```

Generate a non-uniform 2D mesh:

```julia-repl
julia> CartesianMesh((2, 3), ([1.0, 2.0], [0.1, 3.0, 2.5]))
CartesianMesh (2D) with 2x3x1=6 cells
```
