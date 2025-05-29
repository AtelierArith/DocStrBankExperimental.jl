```
SoftRank{is_l2_regularized} <: AbstractRegularized
```

Fast differentiable ranking regularized layer. It uses an L2 regularization if `is_l2_regularized` is true, else it uses an entropic (kl) regularization.

As an [`AbstractRegularized`](@ref) layer, it can also be used for supervised learning with a [`FenchelYoungLoss`](@ref).

# Fields

  * `ε::Float64`: size of the regularization
  * `rev::Bool`: rank in ascending order if false

Reference: [https://arxiv.org/abs/2002.08871](https://arxiv.org/abs/2002.08871)
