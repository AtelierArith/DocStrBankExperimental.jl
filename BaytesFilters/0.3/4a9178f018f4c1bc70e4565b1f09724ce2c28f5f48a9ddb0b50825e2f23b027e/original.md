```julia
struct SemiMarkovTransition{A, B}
```

Transition distributions for state and duration of semi-Markov kernel.

# Fields

  * `state::Any`: Transition distribution of state variable.
  * `duration::Any`: Transition distribution of duration variable.
