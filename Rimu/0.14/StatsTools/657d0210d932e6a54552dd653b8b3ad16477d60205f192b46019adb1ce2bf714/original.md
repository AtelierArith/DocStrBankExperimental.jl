```
rayleigh_replica_estimator_analysis(df::DataFrame; kwargs...)
rayleigh_replica_estimator_analysis(sim::PMCSimulation; kwargs...)
-> (; df_rre, df_se)
```

Compute the [`rayleigh_replica_estimator`](@ref) on a `DataFrame` `df` or [`PMCSimulation`](@ref Main.Rimu.PMCSimulation) `sim` returned from [`solve`](@ref CommonSolve.solve(::ProjectorMonteCarloProblem)) repeatedly over a range of reweighting depths.

Returns a `NamedTuple` with the fields

  * `df_rre`: `DataFrame` with reweighting depth and `rayleigh_replica_estimator` data. See example below.
  * `df_se`: `DataFrame` with [`shift_estimator`](@ref) output, one row per replica

## Keyword arguments

  * `h_range`: The default is about `h_values` values from 0 to twice the estimated correlation time
  * `h_values = 100`: minimum number of reweighting depths
  * `skip = 0`: initial time steps to exclude from averaging
  * `threading = Threads.nthreads() > 1`: if `false` a progress meter is displayed
  * `shift_name = "shift"`: shift data corresponding to column in `df` with names `<shift>_1`, ...
  * `op_name = "Op1"`: name of operator overlap corresponding to column in `df` with names `c1_<op_ol>_c2`, ...
  * `vec_name = "dot"`: name of vector-vector overlap corresponding to column in `df` with names `c1_<vec_ol>_c2`, ...
  * `Anorm = 1`: a scalar prefactor to scale the operator overlap data
  * `warn = true`: whether to log warning messages when blocking fails or denominators are small

## Example

```julia
sim = solve(...)
df_rre, df_se = rayleigh_replica_estimator_analysis(sim; skip=5_000)

using StatsPlots
@df df_rre plot(_ -> se, :h, ribbon = (se_l, se_u), label = "⟨S⟩") # constant line and ribbon for shift estimator
@df df_rre plot!(:h, :val, ribbon = (:val_l, :val_u), label="E_mix") # Rayleigh quotient estimator as a function of reweighting depth
xlabel!("h")
```

See also: [`rayleigh_replica_estimator`](@ref), [`mixed_estimator_analysis`](@ref), [`AllOverlaps`](@ref Main.AllOverlaps).
