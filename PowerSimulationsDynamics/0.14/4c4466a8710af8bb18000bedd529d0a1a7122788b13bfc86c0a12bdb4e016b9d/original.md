```
function PerturbState(
    time::Float64,
    index::Int,
    value::Float64,
)
```

Allows the user to modify the state `index` by adding `value`. The user should modify dynamic states only, since algebraic state may require to do a reinitialization.

# Arguments:

  * `time::Float64` : Defines when the modification of the state will happen. This time should be inside the time span considered in the Simulation.
  * `index::Int` : Defines which state index you want to modify
  * `value::Float64` : Defines how much the state will increase in value
