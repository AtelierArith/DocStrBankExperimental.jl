```
state_vectors(state::ReplicaState)
state_vectors(sim::PMCSimulation)
```

Return an `r×s` `AbstractMatrix` of configuration vectors from the `state`, or the result of [`solve(::ProjectorMonteCarloProblem)`](@ref). The vectors can be accessed by indexing the resulting collection, where the row index corresponds to the replica index and the column index corresponds to the spectral state index.

See also [`ProjectorMonteCarloProblem`](@ref), [`Rimu.PMCSimulation`](@ref), [`Rimu.SingleState`](@ref), [`Rimu.ReplicaState`](@ref), [`Rimu.SpectralState`](@ref).
