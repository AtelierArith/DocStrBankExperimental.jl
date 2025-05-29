```julia
mutable struct Accumulator
```

Mutable iterator struct that can be stored and updated in immutable structs. Contains cumulative and current value of input.

# Fields

  * `cumulative::Float64`: Cumulative value of all inputs.
  * `current::Float64`: Current input value.
