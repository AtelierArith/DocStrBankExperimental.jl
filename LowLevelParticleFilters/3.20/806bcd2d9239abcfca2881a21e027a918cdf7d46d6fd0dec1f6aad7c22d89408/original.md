```
combine!(imm::IMM)
```

Combine the models of the IMM filter into a single state `imm.x` and covariance `imm.R`. This is done by taking a weighted average of the states and covariances of the individual models, where the weights are the mixing probabilities `μ`.
