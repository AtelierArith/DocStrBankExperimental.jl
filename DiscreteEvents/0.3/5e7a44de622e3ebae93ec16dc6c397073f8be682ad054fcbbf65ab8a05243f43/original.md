```
periodic!([clk], ex, Δt; <keyword arguments>)
periodic!(clk, ex; <keyword arguments>)
```

Register an Action `ex` for periodic execution at the clock`s sample rate.

# Arguments

  * `clk<:AbstractClock`: if not supplied, it registers on 𝐶,
  * `ex<:Action`: an expression or function or a tuple of them,
  * `Δt<:Number=clk.Δt`: set the clock's sampling rate, if no Δt is given, it takes   the current sampling rate, if ≤ 0, it calculates a positive one,

# Keyword arguments

  * `cid::Int=clk.id`: if cid ≠ clk.id, sample at the parallel clock   with id == cid. This overrides `spawn`,
  * `spawn::Bool=false`: if true, spawn the periodic event to other available threads.
