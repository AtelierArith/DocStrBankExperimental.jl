```
get_dimers(smld::BasicSMLD)
```

Extract a new BasicSMLD containing only emitters in dimer state.

# Arguments

  * `smld::BasicSMLD`: Original SMLD with all emitters

# Returns

  * `BasicSMLD`: New SMLD containing only dimers

# Example

```julia
# Extract only dimers from simulation results
smld = simulate(params)
dimer_smld = get_dimers(smld)
```
