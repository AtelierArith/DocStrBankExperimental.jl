```
rayleigh_replica_estimator(
    op_ol, vec_ol, shift, h, time_step;
    skip = 0,
    E_r = mean(shift[skip+1:end]),
    weights = w_exp,
    kwargs...
)
rayleigh_replica_estimator(
    df::DataFrame;
    shift_name="shift",
    op_name="Op1",
    vec_name="dot",
    h=0,
    skip=0,
    Anorm=1,
    kwargs...
)
rayleigh_replica_estimator(sim::PMCSimulation; kwargs...)
-> r::RatioBlockingResult
```

Compute the estimator of a Rayleigh quotient of operator $\hat{A}$ with reweighting,

$$
A_\mathrm{est}(h) = \frac{\sum_{a<b} \sum_n w_{h,a}^{(n)} w_{h,b}^{(n)}
    \mathbf{c}_a^{(n)} \cdot \hat{A} \cdot \mathbf{c}_b^{(n)}}
    {\sum_{a<b} \sum_n w_{h,a}^{(n)} w_{h,b}^{(n)} \mathbf{c}_a^{(n)} \cdot \mathbf{c}_b^{(n)}},
$$

using data from multiple replicas.

Argument `op_ol` holds data for the operator overlap $\mathbf{c}_a^{(n)} \hat{A} \mathbf{c}_b^{(n)}$ and `vec_ol` holds data for the vector overlap $\mathbf{c}_a^{(n)} \mathbf{c}_b^{(n)}$. They are of type `Vector{Vector}`, with each element `Vector` holding the data for a pair of replicas. Argument `shift` is of type `Vector{Vector}`, with each element `Vector` holding the shift data for each individual replica.

The second method computes the Rayleigh quotient directly from a `DataFrame` or [`PMCSimulation`](@ref Main.Rimu.PMCSimulation) returned by [`solve`](@ref CommonSolve.solve(::ProjectorMonteCarloProblem)). The keyword arguments `shift_name`, `op_name` and `vec_name` can be used to change the names of the relevant columns, see [`AllOverlaps`](@ref Main.AllOverlaps) for default formatting. The operator overlap data can be scaled by a prefactor `Anorm`. A specific reweighting depth can be set with keyword argument `h`. The default is `h = 0` which calculates the Rayleigh quotient without reweighting.

The reweighting is an extension of the mixed estimator using the reweighting technique described in [Umrigar *et al.* (1993)](http://dx.doi.org/10.1063/1.465195). Reweighting is done over `h` time steps and `length(shift) - skip` time steps are used for the blocking analysis done with [`ratio_of_means`](@ref). `weights` is a function that calulates the weights. See [`w_exp`](@ref) and [`w_lin`](@ref). Additional keyword arguments are passed on to [`ratio_of_means`](@ref).

Error propagation is done with [`MonteCarloMeasurements`](https://github.com/baggepinnen/MonteCarloMeasurements.jl). Results are returned as [`RatioBlockingResult`](@ref).

See also [`mixed_estimator`](@ref), [`growth_estimator`](@ref).
