```
sample_time!([clk::Clock], Δt::N) where {N<:Number}
```

Set the clock's sample rate starting from now (`tau(clk)`).

# Arguments

  * `clk::Clock`: if not supplied, set the sample rate on 𝐶,
  * `Δt::N`: sample rate, time interval for sampling
