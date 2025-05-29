```
SemLoss(args...; loss_weights = nothing, ...)
```

Constructs the loss field of a SEM. Can contain multiple `SemLossFunction`s, the model is optimized over their sum. See also [`SemLossFunction`](@ref).

# Arguments

  * `args...`: Multiple `SemLossFunction`s.
  * `loss_weights::Vector`: Weights for each loss function. Defaults to unweighted optimization.

# Examples

```julia
my_ml_loss = SemML(...)
my_ridge_loss = SemRidge(...)
my_loss = SemLoss(SemML, SemRidge; loss_weights = [1.0, 2.0])
```
