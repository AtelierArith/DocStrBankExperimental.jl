```
growth_estimator(
    shift, wn, h, time_step;
    skip = 0,
    E_r = mean(shift[skip+1:end]),
    weights = w_exp,
    change_type = identity,
    kwargs...
)
growth_estimator(
    df::DataFrame, h;
    shift_name=:shift,
    norm_name=:norm,
    time_step=determine_constant_time_step(df),
    kwargs...
)
growth_estimator(sim::PMCSimulation; kwargs...)
-> r::RatioBlockingResult
```

Compute the growth estimator with reference energy `E_r` by the reweighting technique described in [Umrigar *et al.* (1993)](http://dx.doi.org/10.1063/1.465195), see Eq. (20). `shift` and `wn` are equal length vectors containing the shift and walker number time series, respectively.  Reweighting is done over `h` time steps and `length(shift) - skip` time steps are used for the blocking analysis done with [`ratio_of_means`](@ref). `weights` is a function that calulates the weights. See [`w_exp`](@ref) and [`w_lin`](@ref).

$$
E_{gr} = E_r - \frac{1}{dτ}\ln
    \frac{\sum_n w_{h+1}^{(n+1)} N_\mathrm{w}^{(n+1)}}
        {\sum_m w_{h}^{(m)} N_\mathrm{w}^{(m)}} ,
$$

where $dτ$ is the `time_step`

When `h` is greater than the autocorrelation time scale of the `shift`, then `E_gr` (returned as `r.ratio`) is an unbiased but approximate estimator for the ground state energy $E_0$ with an error $\mathcal{O}(dτ^2)$ and potentially increased confidence intervals compared to the (biased) shift estimator.  Error propagation is done with [`MonteCarloMeasurements`](https://github.com/baggepinnen/MonteCarloMeasurements.jl). Propagation through the logarithm can be modified by setting `change_type` to [`to_measurement`](@ref) in order to avoid `NaN` results from negative outliers.

If `success==true` the blocking analysis was successful in `k-1` steps, using `blocks` uncorrelated data points.

The second method calculates the growth estimator directly from a [`PMCSimulation`](@ref Main.Rimu.PMCSimulation) or `DataFrame` returned by [`solve`](@ref CommonSolve.solve(::ProjectorMonteCarloProblem)). The keyword arguments `shift_name` and `norm_name` can be used to change the names of the relevant columns.

See also [`mixed_estimator`](@ref) and [`RatioBlockingResult`](@ref).
