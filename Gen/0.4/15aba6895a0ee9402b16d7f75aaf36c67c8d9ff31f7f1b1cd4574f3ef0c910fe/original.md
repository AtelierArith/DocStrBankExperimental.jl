```
categorical(probs::AbstractArray{U, 1}) where {U <: Real}
```

Given a vector of probabilities `probs` where `sum(probs) = 1`, sample an `Int` `i` from the set {1, 2, .., `length(probs)`} with probability `probs[i]`.
