```
get_state_series(
    res::SimulationResults,
    ref::Tuple{String, Symbol};
    dt::Union{Nothing, Float64, Vector{Float64}} = nothing
)
end
```

Function to obtain series of states out of DAE Solution.

# Arguments

  * `res::SimulationResults` : Simulation Results object that contains the solution
  * `ref:Tuple{String, Symbol}` : Tuple used to identify the dynamic device, via its name, as a `String`, and the associated state as a `Symbol`.
