```
demodulate(x, f0, NW, blockLen; <keyword arguments>)
```

Multitaper complex demodulation

...

# Arguments

  * `x::Vector{T} where T<:Float64`: the vector containing the time series
  * `f0::Float64`: center frequency for the complex demodulate
  * `NW::Float64`: the time bandwidth product
  * `blockLen::Int64`: the length of the blocks to use
  * `wrapphase::Bool = true`: whether or not to unwrap the phase
  * `dt::Float64 = 1.0`: the sampling rate of the series, in time units
  * `basetime::Float64 = 0.0`: the time at which the time series begins

...

...

# Outputs

  * A struct of type `Demodulate`

...
