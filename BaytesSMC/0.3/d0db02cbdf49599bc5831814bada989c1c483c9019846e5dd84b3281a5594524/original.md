```julia
struct SMCDefault{F<:Function, T<:BaytesCore.ResamplingMethod, B<:BaytesCore.UpdateBool, C<:BaytesCore.UpdateBool, U<:BaytesCore.UpdateBool}
```

Default arguments for SMC constructor.

# Fields

  * `Ntuning::Int64`: Number of tuning steps used when constructing sampler.
  * `resamplingmethod::BaytesCore.ResamplingMethod`: Threshold for resampling chains.
  * `resamplingthreshold::Float64`: Threshold for resampling chains. Set to 1.0 if resampling should always be applied.
  * `jitterfun::Function`: Function that is applied to correlation vector of parameter to determine if jittering can be stopped.
  * `jitteradaption::BaytesCore.UpdateBool`: Boolean if fixed number of jittersteps are applied or jittering is based on parameter correlation.
  * `jitterdiagnostics::BaytesCore.UpdateBool`: Boolean if diagnostics in jittersteps should be recorded in SMCDiagnostics.
  * `jitterthreshold::Float64`: Stopping threshold against jitterfun(correlation) of jittered model parameter.
  * `jittermin::Int64`: Minimum number of jittering steps.
  * `jittermax::Int64`: Maximum number of jittering steps.
  * `generated::BaytesCore.UpdateBool`: Boolean if generate(_rng, objective) for corresponding model is stored in PF Diagnostics.
