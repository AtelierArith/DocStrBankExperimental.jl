```
mixed_estimator_analysis(df::DataFrame; kwargs...)
mixed_estimator_analysis(sim::PMCSimulation; kwargs...)
-> (; df_me, correlation_estimate, se, se_l, se_u)
```

Compute the [`mixed_estimator`](@ref) on a `DataFrame` `df` or [`PMCSimulation`](@ref Main.Rimu.PMCSimulation) `sim` returned from [`solve`](@ref CommonSolve.solve(::ProjectorMonteCarloProblem)) repeatedly over a range of reweighting depths.

Returns a `NamedTuple` with the fields

  * `df_me`: `DataFrame` with reweighting depth and `mixed_estiamator` data. See example below.
  * `correlation_estimate`: estimated correlation time from blocking analysis
  * `se, se_l, se_u`: [`shift_estimator`](@ref) and error

## Keyword arguments

  * `h_range`: The default is about `h_values` values from 0 to twice the estimated correlation time
  * `h_values = 100`: minimum number of reweighting depths
  * `skip = 0`: initial time steps to exclude from averaging
  * `threading = Threads.nthreads() > 1`: if `false` a progress meter is displayed
  * `shift_name = :shift` name of column in `df` with shift data
  * `hproj_name = :hproj` name of column in `df` with operator overlap data
  * `vproj_name = :vproj` name of column in `df` with projector overlap data
  * `warn = true` whether to log warning messages when blocking fails or denominators are small

## Example

```julia
sim = solve(...)
df_me, correlation_estimate, se, se_l, se_u = mixed_estimator_analysis(sim; skip=5_000)

using StatsPlots
@df df_me plot(_ -> se, :h, ribbon = (se_l, se_u), label = "⟨S⟩") # constant line and ribbon for shift estimator
@df df_me plot!(:h, :val, ribbon = (:val_l, :val_u), label="E_mix") # mixed estimator as a function of reweighting depth
xlabel!("h")
```

See also: [`mixed_estimator`](@ref), [`growth_estimator_analysis`](@ref).
