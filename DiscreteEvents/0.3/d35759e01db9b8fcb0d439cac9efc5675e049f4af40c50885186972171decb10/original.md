```
resetClock!(clk::Clock, Δt::T=0.01; t0::U=0; <keyword arguments>) where {T<:Number, U<:Number}
```

Reset a clock.

# Arguments

  * `clk::Clock`
  * `Δt::T=0.01`: sample rate
  * `t0::Float64=0` or `t0::Time`: start time
  * `hard::Bool=true`: time is reset, all scheduled events and sampling are   deleted. If hard=false, then only time is reset, event and   sampling times are adjusted accordingly.
  * `unit=NoUnits`: the Time unit for the clock after reset. If a `Δt::Time` is   given, its Time unit goes into the clock Time unit. If only t0::Time is given,   its Time unit goes into the clock time unit.

# Examples

```jldoctest
julia> using DiscreteEvents, Unitful

julia> import Unitful: s

julia> c = Clock(1s, t0=60s)
Clock 1: state=:idle, t=60.0s, Δt=1.0s, prc:0
  scheduled ev:0, cev:0, sampl:0

julia> resetClock!(c)
"clock reset to t₀=0.0, sampling rate Δt=0.01."

julia> c
Clock 1: state=:idle, t=0.0, Δt=0.01, prc:0
  scheduled ev:0, cev:0, sampl:0
```
