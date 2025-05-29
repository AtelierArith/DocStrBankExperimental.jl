```
ll, lls, rest = correct!(imm::IMM, u, y, args; kwargs)
```

The correct step of the IMM filter corrects each model with the measurements `y` and control input `u`. The mixing probabilities `imm.μ` are updated based on the likelihood of each model given the measurements and the transition probability matrix `P`.

The returned tuple consists of the sum of the log-likelihood of all models, the vector of individual log-likelihoods and an array of the rest of the return values from the correct step of each model.
