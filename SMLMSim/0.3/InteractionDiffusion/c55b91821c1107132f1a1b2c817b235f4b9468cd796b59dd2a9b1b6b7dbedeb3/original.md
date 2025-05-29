```
extract_final_state(smld::SMLD)
```

Extract the emitters from the final frame of a simulation to use as starting conditions.

# Arguments

  * `smld::SMLD`: SMLD containing emitters from a simulation

# Returns

  * `Vector{<:AbstractEmitter}`: Emitters from the final frame

# Example

```julia
# Run a simulation
params = DiffusionSMLMParams(t_max=5.0)
smld = simulate(params)

# Extract final state
final_state = extract_final_state(smld)

# Continue simulation with new parameters
params_new = DiffusionSMLMParams(t_max=10.0, diff_monomer=0.2)
smld_continued = simulate(params_new; starting_conditions=final_state)
```
