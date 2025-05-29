```
calc_rasterstate(sim, raster::Symbol, f, f_returns::DataType = Nothing, ::Type{T} = Nothing)
```

Combined calc_raster with agentstate for the cells of the raster.

Calculate values for the raster `raster` by applying `f` to the state of each cell.

`f_returns` must be the type returned by the function f. There must be an implementation of the zero function for this type, and zero(returntype) + f(state) must be equal to f(state). In the event that all cells in the raster returns the same `DataType`, `f_returns` can be set to `Nothing`, in which case `f_returns` is automatically derived.

`T` can be set to `Nothing`, this decreases the performance, but is necessary in the unusual case that a raster contains different types of agents (in this case `agentstate_flexible` is used instead of `agentstate`).

Returns a n-dimensional array (with the same dimensions as `raster`) with those values.

Example:

Instead of

```@example
    calc_raster(sim, :raster, id -> agentstate(sim, id, Cell).active, Bool, [ Cell ]) 
```

it also possible to just write

```@example
    calc_rasterstate(sim, :raster, c -> c.active, Bool, Cell)
```

Can be only called after [`finish_init!`](@ref).

See also [`add_raster!`](@ref), [`calc_rasterstate`](@ref) and [`rastervalues`](@ref)
