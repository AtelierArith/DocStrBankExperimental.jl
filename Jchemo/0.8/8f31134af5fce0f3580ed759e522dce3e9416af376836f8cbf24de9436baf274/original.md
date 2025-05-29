```
predict(object::Rrda, X; lb = nothing)
```

Compute Y-predictions from a fitted model.

  * `object` : The fitted model.
  * `X` : X-data for which predictions are computed.
  * `lb` : Regularization parameter, or collection of regularization parameters,    "lambda" to consider. If nothing, it is the parameter stored in the    fitted model.
