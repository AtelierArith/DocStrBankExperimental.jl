```
Tucker(X::NEAT, Y::NEAT; w₁ = length(X.rawX) / (length(X.rawX) + length(Y.rawX)), w₂ = 1.0 - w₁)
```

Tucker observed score method.
