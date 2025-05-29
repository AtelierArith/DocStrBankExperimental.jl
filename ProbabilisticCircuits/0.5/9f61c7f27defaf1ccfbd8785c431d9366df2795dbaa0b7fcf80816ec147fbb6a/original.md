```
loglikelihoods(pc::ProbCircuit, data::Matrix)
```

Computes loglikelihoods of the `circuit` over the `data` on cpu. Linearizes the circuit and computes the marginals in batches.
