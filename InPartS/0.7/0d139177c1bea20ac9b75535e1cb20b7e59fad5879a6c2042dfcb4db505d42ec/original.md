```
ExponentialBackoffCallback(; kwargs...) <: AbstractCallback
```

Returns a callback that triggers on first execution and then every `interval` seconds. Where `interval` is multiplied by `factor` after each execution, but never exceeds `max_interval`.

Starts back at `start_interval` after `defrost!` is called.

## keyword arguments

  * `start_interval`: initial interval in seconds
  * `max_interval=Inf`: maximum interval in seconds
  * `factor=2`: factor by which the interval is multiplied after each execution
  * `affect`: function to execute
  * `interrupt=Returns(nothing)`: function to execute when simulation is interrupted
  * `finalize=Returns(nothing)`: function to execute when simulation is finalized

`affect`, `interrupt`, and `finalize` must accept an `InPartS.DynamicState` as argument.
