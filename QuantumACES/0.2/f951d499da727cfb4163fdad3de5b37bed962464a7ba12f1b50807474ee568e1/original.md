```
simulate_stim_ensemble(d_rand::RandDesign, stim_ensemble::Vector{Vector{String}}, experiment_shots::Integer; seed::Union{UInt64, Nothing} = nothing, diagnostics::Bool = true)
```

Saves data simulated with Stim for the randomised experimental design `d_rand` with an associated ensemble of Stim circuits `stim_ensemble` produced by [`get_stim_qiskit_ensemble`](@ref), with `experiment_shots` shots for each circuit. The simulation uses the random seed `seed` and displays diagnostics if `diagnostics` is `true`.
