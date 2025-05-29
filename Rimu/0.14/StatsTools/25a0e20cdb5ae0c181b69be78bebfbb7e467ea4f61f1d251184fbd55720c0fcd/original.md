```
replica_fidelity(df::DataFrame; p_field = :hproj, skip = 0)
replica_fidelity(sim::PMCSimulation; kwargs...)
```

Compute the fidelity of the average coefficient vector and the projector defined in `p_field` from the [`PMCSimulation`](@ref Main.Rimu.PMCSimulation) or `DataFrame` returned by solve, using replicas `_1` and `_2`. Calls [`ratio_of_means`](@ref) to perform a blocking analysis on a ratio of the means of separate time series and returns a [`RatioBlockingResult`](@ref). The first `skip` steps in the time series are skipped.

The fidelity of states `|ψ⟩` and `|ϕ⟩` is defined as

$$
F(ψ,ϕ) = \frac{|⟨ψ|ϕ⟩|^2}{⟨ψ|ψ⟩⟨ϕ|ϕ⟩} .
$$

Specifically, `replica_fidelity` computes

$$
F(\mathbf{v},⟨\mathbf{c}⟩) =
    \frac{⟨(\mathbf{c}_1⋅\mathbf{v})(\mathbf{v}⋅\mathbf{c}_1)⟩}
    {⟨\mathbf{c}_1⋅\mathbf{c}_1⟩} ,
$$

where `v` is the projector specified by `p_field`, which is assumed to be normalised to unity with the two-norm (i.e. `v⋅v == 1`), and $\mathbf{c}_1$ and $\mathbf{c}_2$ are two replica coefficient vectors.
