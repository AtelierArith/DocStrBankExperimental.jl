```
CTMC{T<:AbstractFloat, U<:Int}
```

A Continuous Time Markov Chain representation storing the full trajectory of state transitions.

# Fields

  * `simulation_time::T`: Total simulation time span
  * `transition_times::Vector{T}`: Time points at which state changes occurred, starting at 0.0
  * `states::Vector{U}`: Sequence of states entered at each transition time, starting with initial state

# Type Parameters

  * `T`: Floating point type for time values
  * `U`: Integer type for state indices

# Note

The `states` and `transition_times` vectors have the same length, with each entry in `states[i]` representing the state entered at time `transition_times[i]`. The system remains in `states[i]`  until time `transition_times[i+1]`.
