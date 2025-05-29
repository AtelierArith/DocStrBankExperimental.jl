```
FrequencyEstimation(X::NEAT, Y::NEAT; w₁ = length(X.rawX) / (length(X.rawX) + length(Y.rawX)), w₂ = 1.0 - w₁)
```

Conduct frequency estimation equipercentile equating, which assumes, for both form, the conditional distribution of total score given each common part score is the same in both populations.
