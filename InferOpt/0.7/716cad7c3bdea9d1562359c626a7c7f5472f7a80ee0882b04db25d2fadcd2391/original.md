```
SoftSort{is_l2_regularized} <: AbstractOptimizationLayer
```

Fast differentiable sorting optimization layer. It uses an L2 regularization if `is_l2_regularized` is true, else it uses an entropic (kl) regularization.

Reference [https://arxiv.org/abs/2002.08871](https://arxiv.org/abs/2002.08871)

# Fields

  * `ε::Float64`: size of the regularization
  * `rev::Bool`: sort in ascending order if false
