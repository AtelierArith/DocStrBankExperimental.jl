```
estimate_value(estimator, mdp, state, remaining_depth)
```

Return an estimate of the value.

The `remaining_depth` argument indicates the remaining number of steps from the point where `estimate_value` is called to the `depth` argument of the MCTS solver. It can be safely ignored, but can be used to limit rollouts to a fixed horizon from the *root node*.
