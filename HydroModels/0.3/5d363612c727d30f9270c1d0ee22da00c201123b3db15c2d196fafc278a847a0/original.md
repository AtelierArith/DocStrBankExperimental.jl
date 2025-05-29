```
@hydroroute name begin ... end
```

Macro to simplify the construction of a `HydroRoute` object.

# Usage

```julia
@hydroroute :my_route begin
    fluxes = [
        @hydroflux outflow ~ k * storage
    ]
    dfluxes = [
        @stateflux storage ~ inflow - outflow
    ]
    aggr_func = identity # or other function
end
```

Defines a `HydroRoute` with the specified name (`:my_route`), fluxes, state derivatives (`dfluxes`), and aggregation function (`aggr_func`) within the `begin...end` block.

# Arguments

  * `name`: (Optional) Symbol for the route name.
  * `block`: A `begin...end` block containing assignments for `fluxes`, `dfluxes`, and `aggr_func`.

# Returns

  * A `HydroRoute` instance.
