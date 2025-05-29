```
calc_raster(sim, raster::Symbol, f, f_returns::DataType, accessible::Vector{DataType})
```

Calculate values for the raster `raster` by applying `f` to each cell ID of the cells constructed by the `add_raster!` function.

`f_returns` must be the type returned by the function f. There must be an implementation of the zero function for this type, and zero(returntype) | f(id) must be equal to f(id).

`accessible` is a vector of Agent and/or Edge types. This vector must list all types that are accessed directly (e.g. via [`agentstate`](@ref) or indirectly (e.g. via [`neighborstates`](@ref) in the transition function.

If the results of `calc_raster` depend only on the state of the cells (as in the following example) and all cells have the same type, [`calc_rasterstate`](@ref) can be used as concise alternatives.

Returns a n-dimensional array (with the same dimensions as `raster`) with those values.

Example:

The following code from a "Game of Life" implementation generates a boolean matrix indicating which cells are alive (and therefore maps the internal graph structure to the usual representation of a cellular automaton):

```@example
    calc_raster(sim, :raster, id -> agentstate(sim, id, Cell).active, Bool, [ Cell ]) 
```

Can be only called after [`finish_init!`](@ref).

See also [`add_raster!`](@ref) and [`calc_rasterstate`](@ref)
