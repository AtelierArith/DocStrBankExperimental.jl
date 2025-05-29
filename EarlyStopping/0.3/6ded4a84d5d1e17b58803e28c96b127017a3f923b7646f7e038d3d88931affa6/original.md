```
TimeLimit(; t=0.5)
```

An early stopping criterion for loss-reporting iterative algorithms. 

Stopping is triggered after `t` hours have elapsed since the stopping criterion was initiated.

Any Julia built-in `Real` type can be used for `t`. Subtypes of `Period` may also be used, as in `TimeLimit(t=Minute(30))`.

Internally, `t` is rounded to nearest millisecond. ``
