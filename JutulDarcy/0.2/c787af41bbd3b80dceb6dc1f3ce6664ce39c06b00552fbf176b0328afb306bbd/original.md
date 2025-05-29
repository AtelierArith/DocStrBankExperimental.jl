```
simulate_reservoir(state0, model, dt;
    parameters = setup_parameters(model),
    restart = false,
    forces = setup_forces(model),
    kwarg...
)
simulate_reservoir(case;
    kwarg...
)
```

Convenience function for simulating a reservoir model. This function internally calls [`setup_reservoir_simulator`](@ref), simulates the problem and returns a [`ReservoirSimResult`](@ref). Keyword arguments are passed onto [`setup_reservoir_simulator`](@ref) and are documented in that function.

You can optionally unpack this result into the most typical desired outputs:

`wellsols, states = simulate_reservoir(...)`

where `wellsols` contains the well results and `states` the reservoir results (pressure, saturations and so on, in each cell of the reservoir domain).

# Examples

You can restart/resume simulations by both providing the `output_path` argument and the `restart` argument:

```
# Automatically restart from last solved step and returning the outputs if the simulation was already solved.
result = simulate_reservoir(state0, model, dt, output_path = "/some/path", restart = true)

# Restart from step 5
result = simulate_reservoir(state0, model, dt, output_path = "/some/path", restart = 5)

# Start from the beginning (default)
result = simulate_reservoir(state0, model, dt, output_path = "/some/path", restart = false)
```
