```
AdaGrad(η = 1f-1, ϵ = eps(typeof(η)))
```

[AdaGrad](http://www.jmlr.org/papers/volume12/duchi11a/duchi11a.pdf) optimizer. It has parameter specific learning rates based on how frequently it is updated. Parameters don't need tuning.

# Parameters

  * Learning rate (`η`): Amount by which gradients are discounted before updating                      the weights.
  * Machine epsilon (`ϵ`): Constant to prevent division by zero                        (no need to change default)
