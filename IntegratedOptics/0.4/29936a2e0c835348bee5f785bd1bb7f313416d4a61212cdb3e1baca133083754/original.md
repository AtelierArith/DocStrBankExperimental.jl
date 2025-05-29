```
ADAGrad(η = 0.1)
```

[ADAGrad](http://www.jmlr.org/papers/volume12/duchi11a/duchi11a.pdf) optimizer. It has parameter specific learning rates based on how frequently it is updated. Parameters don't need tuning.

# Parameters

  * Learning rate (`η`): Amount by which gradients are discounted before updating                      the weights.

# Examples

```julia
opt = ADAGrad()
opt = ADAGrad(0.001)
```
