```
sample(pc::ProbCircuit, num_samples, data::Matrix;; batch_size, rng = default_rng())
```

Generate `num_samples` from the joint distribution of the circuit conditioned on the `data`.
