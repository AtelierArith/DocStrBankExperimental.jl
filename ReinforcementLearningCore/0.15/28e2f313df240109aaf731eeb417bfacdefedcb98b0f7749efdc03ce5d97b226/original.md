```
QBasedPolicy(;learner, explorer)
```

Wraps a learner and an explorer. The learner is a struct that should predict the Q-value of each legal action of an environment at its current state. It is typically a table or a neural network.  QBasedPolicy can be queried for an action with `RLBase.plan!`, the explorer will affect the action selection accordingly.
