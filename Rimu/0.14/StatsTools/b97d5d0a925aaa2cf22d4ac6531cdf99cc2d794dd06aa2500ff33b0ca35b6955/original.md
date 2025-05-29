```
mixed_estimator(
    hproj, vproj, shift, h, time_step;
    skip = 0,
    E_r = mean(shift[skip+1:end]),
    weights = w_exp,
    kwargs...
)
mixed_estimator(
    df::DataFrame, h;
    hproj_name=:hproj,
    vproj_name=:vproj,
    shift_name=:shift,
    time_step=determine_constant_time_step(df),
    kwargs...
)
mixed_estimator(sim::PMCSimulation, h; kwargs...)
-> r::RatioBlockingResult
```

Compute the mixed estimator by the reweighting technique described in [Umrigar *et al.* (1993)](http://dx.doi.org/10.1063/1.465195), Eq. (19)

$$
E_\mathrm{mix} = \frac{\sum_n w_{h}^{(n)}  (Ĥ'\mathbf{v})⋅\mathbf{c}^{(n)}}
        {\sum_m w_{h}^{(m)}  \mathbf{v}⋅\mathbf{c}^{(m)}} ,
$$

where the time series `hproj ==` $(Ĥ'\mathbf{v})⋅\mathbf{c}^{(n)}$ and `vproj ==` $\mathbf{v}⋅\mathbf{c}^{(m)}$ have the same length as `shift` (See [`ProjectedEnergy`](@ref Main.ProjectedEnergy) on how to set these up).  Reweighting is done over `h` time steps and `length(shift) - skip` time steps are used for the blocking analysis done with [`ratio_of_means`](@ref). `weights` is a function that calulates the weights. See [`w_exp`](@ref) and [`w_lin`](@ref).  Additional keyword arguments are passed on to [`ratio_of_means`](@ref).

When `h` is greater than the autocorrelation time scale of the `shift`, then `r.ratio` is an unbiased but approximate estimator for the ground state energy $E_0$ with an error $\mathcal{O}(dτ^2)$, where $dτ$ is the `time_step`, and potentially increased confidence intervals compared to the unweighted ratio.  Error propagation is done with [`MonteCarloMeasurements`](https://github.com/baggepinnen/MonteCarloMeasurements.jl). Results are returned as [`RatioBlockingResult`](@ref).

The second method calculates the mixed energy estimator directly from a `DataFrame` or [`PMCSimulation`](@ref Main.Rimu.PMCSimulation) returned by [`solve`](@ref CommonSolve.solve(::ProjectorMonteCarloProblem)). The keyword arguments `hproj_name`, `vproj_name`, and `shift_name` can be used to change the names of the relevant columns.

See also [`growth_estimator`](@ref).
