```
Clock{AC} <: AbstractClock
```

A virtual clock structure, used for global and thread local clocks.

# Fields

  * `id::Int`: clock ident number 1: master clock, > 1: parallel clock,
  * `ac::AC`: if id == 1: a [`Vector{ClockChannel}`](@ref ClockChannel) else: [`Ref{ActiveClock}`](@ref ActiveClock),
  * `state::ClockState`: clock state,
  * `time::Float64`: clock time,
  * `unit::FreeUnits`: time unit,
  * `end_time::Float64`: end time for simulation,
  * `Δt::Float64`: sampling time, timestep between ticks,
  * `sc::Schedule`: the clock [`Schedule`](@ref) (events, cond events and sampling),
  * `processes::Dict{Any, Prc}`: registered `Prc`es,
  * `channels::Vector{Channel}`: registered (Actor) channels,
  * `tn::Float64`: next timestep,
  * `tev::Float64`: next event time,
  * `evcount::Int`: event counter,
  * `scount::Int`: sample counter
