```
(timeSignal, signal, signalType) = ModiaResult.rawSignal(result, name)
```

Given the result data structure `result` and a variable `name::AbstractString`, return the result values of the independent variable (= `timeSignal`), the  corresponding result values of the variable (= `signal`) and the type of the signal `signalType::`[`SignalType`](@ref)). Note, an error shall be raised,  if `name` is not known.

The following figure sketches the returned `timeSignal` and `signal` data structures:

![SignalDefinition](https://modiasim.github.io/ModiaResult.jl/resources/images/signal-definition.png)

Other signal types might be mapped to this basic signal type by introducing views.

# Details of the return arguments

`timeSignal::Vector{Vector{T1}}`: A result consists of one or more **segments**. `timeSignal[i][j]` is the value of time instant `j` in segment `i`. `timeSignal[i][:]` must have monotonically increasing values and type `T1<:Real` must be a subtype of `Real` for which a conversion to `AbstractFloat` is defined. For example, `T1::Rational` is fine, but `T1::Complex` is not allowed.

`signal::Vector{Vector{T2}}` or `signal::Vector{Vector{Array{T2,N}}}`: `signal[i][j]` is the value of the variable at time instant `timeSignal[i][j]`. This value can be a scalar or an array. Type `T2` can have one of the following values:

  * `T2 <: Real`, must be a subtype of `Real` for which a conversion to `AbstractFloat`  is defined, or
  * `T2 <: Measurements.Measurement{T1}`, or
  * `T2 <: MonteCarloMeasurements.StaticParticles{T1,N}`, or
  * `T2 <: MonteCarloMeasurements.Particles{T1,N}`.

If the signal is a constant with value `value`, return `([[t_min, t_max]], [[value, value]], ModiaResult.Continuous)`.

If the signal is the time signal, return  `(timeSignal, timeSignal, ModiaResult.independent)`.  The `timeSignal` might be a dummy vector consisting of the first and last time point in the result (if different timeSignals are present for different signals or if the signal is constant).

`signal` and `timeSignal` may have units from package `Unitful`.

The information `signalType::SignalType` defines how the signal can be interpolated and/or plotted. 
