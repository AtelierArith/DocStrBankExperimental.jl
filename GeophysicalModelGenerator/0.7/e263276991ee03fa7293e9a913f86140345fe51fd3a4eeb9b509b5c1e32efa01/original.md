```
Grid = create_CartGrid(; size=(), x = nothing, z = nothing, y = nothing, extent = nothing, CharDim = nothing)
```

Creates a 1D, 2D or 3D cartesian grid of given size. Grid can be created by defining the size and either the `extent` (length) of the grid in all directions, or by defining start & end points (`x`,`y`,`z`). If you specify `CharDim` (a structure with characteristic dimensions created with `GeoParams.jl`), we will nondimensionalize the grd before creating the struct.

Spacing is assumed to be constant in a given direction

This can also be used for staggered grids, as we also create 1D vectors for the central points. The points you indicate in `size` are the corner points.

Note: since this is mostly for solid Earth geoscience applications, the second dimension is called z (vertical)

# Examples

====

A basic case with non-dimensional units:

```julia
julia> Grid = create_CartGrid(size=(10,20),x=(0.,10), z=(2.,10))
Grid{Float64, 2}
           size: (10, 20)
         length: (10.0, 8.0)
         domain: x ∈ [0.0, 10.0], z ∈ [2.0, 10.0]
 grid spacing Δ: (1.1111111111111112, 0.42105263157894735)
```

An example with dimensional units:

```julia
julia> CharDim = GEO_units()
julia> Grid    = create_CartGrid(size=(10,20),x=(0.0km, 10km), z=(-20km, 10km), CharDim=CharDim)
CartGrid{Float64, 2}
           size: (10, 20)
         length: (0.01, 0.03)
         domain: x ∈ [0.0, 0.01], z ∈ [-0.02, 0.01]
 grid spacing Δ: (0.0011111111111111111, 0.0015789473684210528)

```
