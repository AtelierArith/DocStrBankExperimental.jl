```
ConfusionMatrix(pred::Vector{T}, truth::Vector{Bool}, τ::T) where {T <: Number}
```

Given a vector of scores and a vector of ground truths, as well as a threshold, transforms the score into binary predictions and returns the confusion matrix.
