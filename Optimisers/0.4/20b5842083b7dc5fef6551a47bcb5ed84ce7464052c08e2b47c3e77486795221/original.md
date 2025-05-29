```
AdaGrad(η = 0.1, ϵ = 1e-8)
AdaGrad(; [eta, epsilon])
```

[AdaGrad](http://www.jmlr.org/papers/volume12/duchi11a/duchi11a.pdf) optimizer. It has parameter specific learning rates based on how frequently it is updated. Parameters don't need tuning.

# Parameters

  * Learning rate (`η == eta`): Amount by which gradients are discounted before updating                      the weights.
  * Machine epsilon (`ϵ == epsilon`): Constant to prevent division by zero                        (no need to change default)
