```
rastervalues(sim, raster::Symbol, fieldname::Symbol)
```

Creates a matrix with the same dims as the raster `raster` with the values of the field `fieldnames`. All cells of the raster must have  the same type, and also a `zeros` function must exist for the type of `fieldnames`.

Example:

Instead of

```@example
    calc_rasterstate(sim, :raster, c -> c.active, Bool, Cell)
```

it also possible to just write

```@example
    rastervalues(sim, :raster, :active) 
```

Can be only called after [`finish_init!`](@ref).

See also [`add_raster!`](@ref) and [`calc_rasterstate`](@ref)
