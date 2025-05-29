```
NumberLimit(; n=100)
```

An early stopping criterion for loss-reporting iterative algorithms. 

A stop is triggered by `n` consecutive loss updates, excluding "training" loss updates.

If wrapped in a `stopper::EarlyStopper`, this is the number of calls to `done!(stopper)`.
