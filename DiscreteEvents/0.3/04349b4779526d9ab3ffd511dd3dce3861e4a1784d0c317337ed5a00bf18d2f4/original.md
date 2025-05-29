```
event!([clk], ex, t; <keyword arguments>)
event!([clk], ex, t, cy; <keyword arguments>)
event!([clk], ex, T, t; <keyword arguments>)
```

Schedule an event for a given time `t`. 

If `t` is a `Distribution`, event time is evaluated as `rand(t)`.   If `cy` is a `Distribution`, the event is repeated after a random  interval `rand(cy)`. If the evaluated time ≤ clk.time, the event  is scheduled at `clk.time`.

# Arguments

  * `clk<:AbstractClock`: clock, it not supplied, the event is scheduled to 𝐶,
  * `ex<:Action`: an expression or function or a tuple of them,
  * `T::Timing`: a timing, one of `at`, `after` or `every`,
  * `t`: event time, `Number` or `Distribution`,
  * `cy`: repeat cycle, `Number` or `Distribution`.

# Keyword arguments

  * `n::Int=typemax(Int)`: number of repeating events,
  * `cid::Int=clk.id`: if cid ≠ clk.id, assign the event to the parallel clock   with id == cid. This overrides `spawn`,
  * `spawn::Bool=false`: if true, spawn the event at other available threads,

# Examples

```jldoctest
julia> using DiscreteEvents, Distributions, Random

julia> Random.seed!(123);

julia> c = Clock()
Clock 1: state=:idle, t=0.0, Δt=0.01, prc:0
  scheduled ev:0, cev:0, sampl:0

julia> f(x) = x[1] += 1
f (generic function with 1 method)

julia> a = [0]
1-element Array{Int64,1}:
 0

julia> event!(c, fun(f, a), 1)                     # 1st event at 1

julia> event!(c, fun(f, a), at, 2)                 # 2nd event at 2

julia> event!(c, fun(f, a), after, 3)              # 3rd event after 3

julia> event!(c, fun(f, a), every, Exponential(3)) # Poisson process with λ=1/3

julia> run!(c, 50)
"run! finished with 26 clock events, 0 sample steps, simulation time: 50.0"

julia> a
1-element Array{Int64,1}:
 26
```
