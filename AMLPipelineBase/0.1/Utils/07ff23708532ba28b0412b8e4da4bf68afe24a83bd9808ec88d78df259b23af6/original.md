```
score(metric::Symbol, actual::Vector, predicted::Vector)
```

Score learner predictions against ground truth values.

Available metrics:

  * :accuracy
  * `metric`: metric to assess with
  * `actual`: ground truth values
  * `predicted`: predicted values

Returns: score of learner
