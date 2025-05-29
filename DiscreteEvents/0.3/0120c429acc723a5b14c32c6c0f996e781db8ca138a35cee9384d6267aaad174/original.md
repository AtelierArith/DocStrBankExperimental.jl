```
@event f(arg...) T t [n]
```

Schedule a function `f(arg...)` as an event to a clock.

# Arguments

  * `f`: function to be executed at event time,
  * `arg...`: its arguments, the first argument must be a clock,
  * `T`: a [`Timing`](@ref) (at, after, every),
  * `t`: a `Number` or a `Distribution`,
  * `n::Int`: repetitions for a repeat event.
