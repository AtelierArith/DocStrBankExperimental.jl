```
PlotData2D(u, semi [or mesh, equations, solver, cache];
           solution_variables=nothing,
           grid_lines=true, max_supported_level=11, nvisnodes=nothing,
           slice=:xy, point=(0.0, 0.0, 0.0))
```

Create a new `PlotData2D` object that can be used for visualizing 2D/3D DGSEM solution data array `u` with `Plots.jl`. All relevant geometrical information is extracted from the semidiscretization `semi`. By default, the primitive variables (if existent) or the conservative variables (otherwise) from the solution are used for plotting. This can be changed by passing an appropriate conversion function to `solution_variables`.

If `grid_lines` is `true`, also extract grid vertices for visualizing the mesh. The output resolution is indirectly set via `max_supported_level`: all data is interpolated to `2^max_supported_level` uniformly distributed points in each spatial direction, also setting the maximum allowed refinement level in the solution. `nvisnodes` specifies the number of visualization nodes to be used. If it is `nothing`, twice the number of solution DG nodes are used for visualization, and if set to `0`, exactly the number of nodes in the DG elements are used.

When visualizing data from a three-dimensional simulation, a 2D slice is extracted for plotting. `slice` specifies the plane that is being sliced and may be `:xy`, `:xz`, or `:yz`. The slice position is specified by a `point` that lies on it, which defaults to `(0.0, 0.0, 0.0)`. Both of these values are ignored when visualizing 2D data.

!!! warning "Experimental implementation"
    This is an experimental feature and may change in future releases.


# Examples

```julia
julia> using Trixi, Plots

julia> trixi_include(default_example())
[...]

julia> pd = PlotData2D(sol)
PlotData2D(...)

julia> plot(pd) # To plot all available variables

julia> plot(pd["scalar"]) # To plot only a single variable

julia> plot!(getmesh(pd)) # To add grid lines to the plot
```
