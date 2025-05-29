```
variational_energy_estimator(shifts, overlaps; kwargs...)
variational_energy_estimator(df::DataFrame; max_replicas=:all, kwargs...)
variational_energy_estimator(sim::PMCSimulation; kwargs...)
-> r::RatioBlockingResult
```

Compute the variational energy estimator from the replica time series of the `shifts` and coefficient vector `overlaps` by blocking analysis. The keyword argument `max_replicas` can be used to constrain the number of replicas processed to be smaller than all available in `df`. Other keyword arguments are passed on to [`ratio_of_means()`](@ref). Returns a [`RatioBlockingResult`](@ref).

An estimator for the variational energy

$$
\frac{⟨\mathbf{c}⟩^† \mathbf{H}⟨\mathbf{c}⟩}{⟨\mathbf{c}⟩^†⟨\mathbf{c}⟩}
$$

is calculated from

$$
Ē_{v}  =  \frac{\sum_{a<b}^R \overline{(S_a+S_b) \mathbf{c}_a^† \mathbf{c}_b}}
               {2\sum_{a<b}^R \overline{\mathbf{c}_a^† \mathbf{c}_b}} ,
$$

where the sum goes over distinct pairs out of the $R$ replicas. See [arXiv:2103.07800](http://arxiv.org/abs/2103.07800).

The `DataFrame` and [`PMCSimulation`](@ref Main.Rimu.PMCSimulation) versions can extract the relevant information from the result of [`solve`](@ref CommonSolve.solve(::ProjectorMonteCarloProblem)). Set up the [`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem) with the keyword argument `replica_strategy = AllOverlaps(R)` and `R ≥ 2`. If passing `shifts` and `overlaps`, the data has to be arranged in the correct order (as provided in the `DataFrame` version).

See [`AllOverlaps`](@ref Main.AllOverlaps).
