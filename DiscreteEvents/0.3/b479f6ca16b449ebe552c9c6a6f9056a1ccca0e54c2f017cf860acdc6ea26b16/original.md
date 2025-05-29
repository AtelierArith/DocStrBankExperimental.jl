```
event!([clk], ex, cond; <keyword arguments>)
```

Schedule `ex` as a conditional event, conditions `cond` get evaluated at each clock tick.

# Arguments

  * `clk<:AbstractClock`: if no clock is supplied, the event is scheduled to 𝐶,
  * `ex<:Action`: an expression or function or a tuple of them,
  * `cond<:Action`: a condition is true if all functions or expressions therein return true,

# Keyword arguments

  * `cid::Int=clk.id`: if cid ≠ clk.id, assign the event to the parallel clock   with id == cid. This overrides `spawn`,
  * `spawn::Bool=false`: if true, spawn the event at other available threads.

# Examples

```jldoctest
julia> using DiscreteEvents

julia> c = Clock()   # create a new clock
Clock 1: state=:idle, t=0.0, Δt=0.01, prc:0
  scheduled ev:0, cev:0, sampl:0

julia> event!(c, fun((x)->println(tau(x), ": now I'm triggered"), c), fun(>=, fun(tau, c), 5))

julia> run!(c, 10)   # sampling is not exact, so it takes 502 sample steps to fire the event
5.009999999999938: now I'm triggered
"run! finished with 0 clock events, 502 sample steps, simulation time: 10.0"
```
