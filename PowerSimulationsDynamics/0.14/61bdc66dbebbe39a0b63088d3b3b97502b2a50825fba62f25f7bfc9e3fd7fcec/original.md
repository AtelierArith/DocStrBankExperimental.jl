```
get_reactivepower_branch_flow(
        res::SimulationResults,
        name::String,
        location::Symbol,
)
```

Function to obtain the reactive power flowing through the series element of a Branch. The user must specified is the power should be computed in the :from or to :bus, by specifying a symbol.

If :from is specified, the power is computed flowing outwards the :from bus. If :to is specified, the power is computed flowing into the :to bus.

# Arguments

  * `res::SimulationResults` : Simulation Results object that contains the solution
  * `name::String` : Name to identify the specified line
  * `location::Symbol` : :from or :to to specify a bus
