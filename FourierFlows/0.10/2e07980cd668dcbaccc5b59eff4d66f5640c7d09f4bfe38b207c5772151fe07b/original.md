```
step_until!(prob, stop_time)
```

Step forward `prob` until `stop_time`.

!!! warn "Fully-explicit timestepping schemes are required"
    We cannot use `step_until!` with [`ETDRK4TimeStepper`](@ref) nor [`FilteredETDRK4TimeStepper`](@ref).


See also: [`stepforward!`](@ref)
