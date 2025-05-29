```
function expectation_value_noisy
```

Get the expectation value of an operator after applying readout error. operators Must be diagonal in the computational basis.

# Arguments

  * `noisy_model`: the simulated noise model
  * `amps`: the probability distribution over computational basis states
  * `op`: desired expectation value
  * `errs`: (optional) error estimates for the probability amplitudes to propagate to

the error in the expectation value
