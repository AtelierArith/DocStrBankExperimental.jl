```
stateptr(mdp::IntervalMarkovDecisionProcess)
```

Return the state pointer of the Interval Markov Decision Process. The state pointer is a vector of integers where the `i`-th element is the index of the first element of the `i`-th state in the transition probability matrix.  I.e. `transition_prob[:, stateptr[j]:stateptr[j + 1] - 1]` is the transition probability matrix for source state `j`.
