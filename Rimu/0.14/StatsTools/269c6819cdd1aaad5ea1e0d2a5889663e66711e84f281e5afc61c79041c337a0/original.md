```
projected_energy(df::DataFrame; skip=0, hproj=:hproj, vproj=:vproj, kwargs...)
projected_energy(sim::PMCSimulation; kwargs...)
-> r::RatioBlockingResult
```

Compute the projected energy estimator

$$
E_\mathrm{p} = \frac{\sum_n  \mathbf{v}⋅Ĥ\mathbf{c}^{(n)}}
        {\sum_m \mathbf{v}⋅\mathbf{c}^{(m)}} ,
$$

where the time series `df.hproj ==` $\mathbf{v}⋅Ĥ\mathbf{c}^{(n)}$ and `df.vproj ==` $\mathbf{v}⋅\mathbf{c}^{(m)}$ are taken from `df`, skipping the first `skip` entries (use `post_step_strategy =`[`ProjectedEnergy`](@ref Main.ProjectedEnergy)`(...)` to set these up in [`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem)). `projected_energy` is equivalent to [`mixed_estimator`](@ref) with `h=0`.

The keyword arguments `hproj` and `vproj` can be used to change the names of the relevant columns. Other `kwargs` are passed on to [`ratio_of_means`](@ref). Returns a [`RatioBlockingResult`](@ref).

See [`NamedTuple`](@ref), [`val_and_errs`](@ref), [`val`](@ref), [`errs`](@ref) for processing results.
