```
init_sim!(s::RamAirKite, measure::Measurement; prn=true, precompile=false) -> Nothing
```

Initialize a kite power system model. 

If a serialized model exists for the current configuration, it will load that model and only update the state variables. Otherwise, it will create a new model from scratch.

# Fast path (serialized model exists):

1. Loads existing ODEProblem from disk
2. Calls `reinit!` to update state variables
3. Sets up integrator with current measurements

# Slow path (no serialized model):

1. Creates symbolic MTK system with all equations
2. Simplifies system equations
3. Creates ODEProblem and serializes to disk
4. Proceeds with fast path

# Arguments

  * `s::RamAirKite`: The kite system state object
  * `measure::Measurement`: Initial state measurements
  * `prn::Bool=true`: Whether to print progress information
  * `precompile::Bool=false`: Whether to build problem for precompilation

# Returns

`Nothing`
