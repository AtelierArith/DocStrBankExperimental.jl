```
StructuredSVMLoss <: AbstractLossLayer
```

Loss associated with the Structured Support Vector Machine, defined by

```
L(θ, y_true) = max_y {δ(y, y_true) + α θᵀ(y - y_true)}
```

Reference: [http://www.nowozin.net/sebastian/papers/nowozin2011structured-tutorial.pdf](http://www.nowozin.net/sebastian/papers/nowozin2011structured-tutorial.pdf) (Chapter 6)

# Fields

  * `aux_loss_maximizer::M`: function of `(θ, y_true, α)` that computes the argmax in the problem above
  * `δ::L`: base loss function
  * `α::Float64`: hyperparameter with a default value of 1.0
