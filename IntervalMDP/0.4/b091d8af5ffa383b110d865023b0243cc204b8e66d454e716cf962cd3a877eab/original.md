```
IntervalMarkovChain(transition_prob::IntervalProbabilities, initial_states::InitialStates = AllStates())
```

Construct an Interval Markov Chain from a square matrix pair of interval transition probabilities. The initial states are optional and if not specified, all states are assumed to be initial states. The number of states is inferred from the size of the transition probability matrix.

The returned type is an `IntervalMarkovDecisionProcess` with only one action per state (i.e. `stateptr[j + 1] - stateptr[j] == 1` for all `j`). This is done to unify the interface for value iteration.
