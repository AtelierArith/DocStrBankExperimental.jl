```
BoundaryFunction(fun; discrete=false, parameters=nothing, reduce_dims=true)
```

Creates a "boundary function" object that can be use to define boundary conditions on fields.

## Arguments

  * `fun`: The function defining the boundary condition.
  * `discrete=false`: If `true`, the boundary function is discrete and has the signature `f(grid, loc, dim, inds...)`.
  * `parameters=nothing`: Optional parameters to be passed to the boundary function.
  * `reduce_dims=true`: If `true`, the boundary function reduces the number of dimensions it operates on. If `false`, the function accepts the same number of coordinates as the number of indices.

## Usage

The example below shows how to use the boundary function to initialise a parabolic profile at the boundary of a 2D grid.

```julia
using Chmy

arch = Arch(CPU())
grid = UniformGrid(arch; origin=(0, 0), extent=(2, 2), dims=(10, 10))

f = Field(arch, grid, Center())
xbc = BoundaryFunction((x, ly) -> x * (ly - x); parameters=(2.0, ))

bc!(arch, grid, f => (x = Dirichlet(xbc), y = Neumann()))
```
