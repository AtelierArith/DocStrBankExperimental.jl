```
interact!(imm::IMM)
```

The interaction step of the IMM filter updates the state and covariance of each internal model based on the mixing probabilities `imm.μ` and the transition probability matrix `imm.P`.

Models with small mixing probabilities will have their states and covariances updated more towards the states and covariances of models with higher mixing probabilities, and vice versa.
