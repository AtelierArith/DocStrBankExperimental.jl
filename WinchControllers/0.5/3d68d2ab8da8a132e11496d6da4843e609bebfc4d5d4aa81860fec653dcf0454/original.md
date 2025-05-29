```
mutable struct Integrator
```

Discrete integrator with external reset.

## Fields

  * `dt::Float64`
  * `i::Float64`: Default: 1.0
  * `output::Float64`: Default: 0.0
  * `last_output::Float64`: Default: 0.0

# Example

```julia
int = Integrator(0.05, 2, 3)      # dt, integration constant, initial output  
input = 2
for i in 1:3
    out = calc_output(int, input) # calculate the output
    println(out)
    on_timer(int)                 # must be called on each time-step
end
reset(int, 3)                     # reset the integrator to the initial state
```
