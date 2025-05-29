```
ImitationLoss <: AbstractLossLayer
```

Generic imitation loss of the form

```
L(θ, t_true) = max_y {δ(y, t_true) + α θᵀ(y - y_true) - (Ω(y) - Ω(y_true))}
```

  * When `δ` is zero, this is equivalent to a [`FenchelYoungLoss`](@ref).
  * When `Ω` is zero, this is equivalent to a [`StructuredSVMLoss`](@ref).

Note: by default, `t_true` is a named tuple with field `y_true`, but it can be any data structure for which the [`get_y_true`](@ref) method is implemented.

# Fields

  * `aux_loss_maximizer`: function of `(θ, t_true, α)` that computes the argmax in the problem above
  * `δ`: base loss function
  * `Ω`: regularization function
  * `α::Float64`: hyperparameter with a default value of 1.0
