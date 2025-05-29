```
delay!(clk, Δt)
delay!(clk, T, t)
```

Delay (suspend) a process for a time interval `Δt` on the clock `clk`.

# Arguments

  * `clk::Clock`,
  * `Δt`: time interval, `Number` or `Distribution`,
  * `T::Timing`: only `until` is accepted,
  * `t`: time delay, `Number` or `Distribution`.
