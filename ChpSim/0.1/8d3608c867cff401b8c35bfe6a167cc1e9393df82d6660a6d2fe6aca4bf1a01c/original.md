```
measure!(state, qubit; rng=GLOBAL_RNG, bias=0.5)
```

Perform a measurement in the Z basis and return the result. If the qubit was in superposition, pick a random result and update the state.

# Arguments

  * `qubit::Int`: The qubit index to measure.
  * `rng::AbstractRNG`: The random number generator to use.
  * `bias::Real`: The artificial probablility of measuring a 1 randomly.
