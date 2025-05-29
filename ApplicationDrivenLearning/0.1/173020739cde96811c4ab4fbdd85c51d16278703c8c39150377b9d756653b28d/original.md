```
compute_cost(model, X, Y, with_gradients=false)
```

Compute the cost function (C) based on the model predictions and the true values.

...

# Arguments

  * `model::ApplicationDrivenLearning.Model`: model to evaluate.
  * `X::Matrix{<:Real}`: input data.
  * `Y::Matrix{<:Real}`: true values.
  * `with_gradients::Bool=false`: flag to compute and return gradients. ...
