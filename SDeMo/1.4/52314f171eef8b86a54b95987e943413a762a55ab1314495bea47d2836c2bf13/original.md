```
ConfusionMatrix(pred::Vector{T}, truth::Vector{Bool}) where {T <: Number}
```

Given a vector of scores and a vector of truth, returns the confusion matrix under the assumption that the score are probabilities and that the threshold is one half.
