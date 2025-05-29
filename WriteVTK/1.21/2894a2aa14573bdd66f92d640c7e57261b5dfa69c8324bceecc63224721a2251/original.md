```
vtk_surface([f::Function], filename, xs, ys, zs; kwargs...)
```

Create unstructured grid file (".vtu") representing a surface plot of a 2D function on coordinates (`xs`, `ys`) with values `zs`.

The coordinates `xs` and `ys` can be given as:

  * 1D arrays of respective dimensions `Nx` and `Ny` (for regular grids);
  * 2D arrays of dimensions `(Nx, Ny)` (for irregular grids).

The values `zs` should be given in a 2D array of dimensions `(Nx, Ny)`.

# Including additional data

Optionally, one can write additional data to the generated file via the function `f`, which works in the same way as for [`vtk_grid`](@ref).

As an example, it is common to colour surface plots by the height `z`. To do this, one should write the `zs` matrix as point data:

```julia
julia> xs = 0:0.5:10; ys = 0:1.0:20;

julia> zs = @. cos(xs) + sin(ys');

julia> vtk_surface("surf", xs, ys, zs) do vtk
           vtk["z_values"] = zs
       end
```

Note that the included data must have dimensions `(Nx, Ny)` (for point data) or `(Nx - 1, Ny - 1)` (for cell data).
