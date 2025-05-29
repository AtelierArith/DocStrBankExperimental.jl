```
stateptr(mdp::MixtureIntervalMarkovDecisionProcess)
```

Return the state pointer of the Interval Markov Decision Process. The state pointer is a vector of integers where the `i`-th element is the index of the first element of the `i`-th state in the transition probability matrix.  I.e. `mixture_probs(transition_prob)[k][l][:, stateptr[j]:stateptr[j + 1] - 1]` is the independent transition probability matrix for (flattened) source state `j` for axis `l` and model `k`, and `mixture_probs(transition_prob)[:, stateptr[j]:stateptr[j + 1] - 1]` is the weighting matrix for `j`.
