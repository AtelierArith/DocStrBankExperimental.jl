```
sat_prob(root::LogicCircuit; varprob::Function)::Rational{BigInt}
```

Get the probability that a random world satisties the circuit.  Probability of each variable is given by `varprob` Function which defauls to 1/2 for every variable.
