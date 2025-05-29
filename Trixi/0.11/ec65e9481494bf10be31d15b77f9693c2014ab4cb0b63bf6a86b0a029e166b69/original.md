```
PlotData1D(u, semi [or mesh, equations, solver, cache];
           solution_variables=nothing, nvisnodes=nothing,
           reinterpolate=Trixi.default_reinterpolate(solver),
           slice=:x, point=(0.0, 0.0, 0.0), curve=nothing)
```

Create a new `PlotData1D` object that can be used for visualizing 1D DGSEM solution data array `u` with `Plots.jl`. All relevant geometrical information is extracted from the semidiscretization `semi`. By default, the primitive variables (if existent) or the conservative variables (otherwise) from the solution are used for plotting. This can be changed by passing an appropriate conversion function to `solution_variables`, e.g., [`cons2cons`](@ref) or [`cons2prim`](@ref).

Alternatively, you can also pass a function `u` with signature `u(x, equations)` returning a vector. In this case, the `solution_variables` are ignored. This is useful, e.g., to visualize an analytical solution. The spatial variable `x` is a vector with one element.

`nvisnodes` specifies the number of visualization nodes to be used. If it is `nothing`, twice the number of solution DG nodes are used for visualization, and if set to `0`, exactly the number of nodes as in the DG elements are used. The solution is interpolated to these nodes for plotting. If `reinterpolate` is `false`, the solution is not interpolated to the `visnodes`, i.e., the solution is plotted at the solution nodes. In this case `nvisnodes` is ignored. By default, `reinterpolate` is set to `false` for `FDSBP` approximations and to `true` otherwise.

When visualizing data from a two-dimensional simulation, a 1D slice is extracted for plotting. `slice` specifies the axis along which the slice is extracted and may be `:x`, or `:y`. The slice position is specified by a `point` that lies on it, which defaults to `(0.0, 0.0)`. Both of these values are ignored when visualizing 1D data. This applies analogously to three-dimensional simulations, where `slice` may be `:xy`, `:xz`, or `:yz`.

Another way to visualize 2D/3D data is by creating a plot along a given curve. This is done with the keyword argument `curve`. It can be set to a list of 2D/3D points which define the curve. When using `curve` any other input from `slice` or `point` will be ignored.

!!! warning "Experimental implementation"
    This is an experimental feature and may change in future releases.

