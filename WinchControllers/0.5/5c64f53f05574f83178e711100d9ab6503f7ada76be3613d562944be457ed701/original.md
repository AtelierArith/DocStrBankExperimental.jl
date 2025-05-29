```
mutable struct UnitDelay
```

UnitDelay, delay the input signal by one time step.

## Fields

  * `last_output::Float64`: Default: 0
  * `last_input::Float64`: Default: 0

# Example

```julia
ud = UnitDelay()
for i in 1:3
    out = calc_output(ud, i) # updates the input and calculates the output
    println(out)
    on_timer(ud)             # next time-step
end
```
