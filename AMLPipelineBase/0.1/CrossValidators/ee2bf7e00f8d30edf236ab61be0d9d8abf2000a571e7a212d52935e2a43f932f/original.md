```
crossvalidate(pl::Machine,X::DataFrame,Y::Vector,pfunc::Function,kfolds=10)
```

Run K-fold crossvalidation where:

  * `pfunc` is a performance metric
  * `X` and `Y` are input and target
