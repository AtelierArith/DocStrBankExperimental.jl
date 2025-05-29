```
@periodic f(arg...) [Δt]
```

Register a function `f(arg...)` for periodic execution at the  clock`s sample rate.

# Arguments

  * `f`: function to be executed periodically,
  * `arg...`: its arguments, the first argument must be a clock,
  * `Δt`: for setting the clock's sample rate.
