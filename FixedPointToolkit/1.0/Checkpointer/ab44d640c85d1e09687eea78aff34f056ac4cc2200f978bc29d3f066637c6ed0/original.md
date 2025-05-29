```julia
save_checkpoint(fileName::String, sc::SelfCons, SelfConsParams::Dict{Symbol, Real})
```

Save the relevant attributed of a `SelfCons` data structure in a JLD2 file `fileName` (`fileName` must end with .jld2).  Also saves some self-consistency parameters like maximum iteration, tolerance etc.
