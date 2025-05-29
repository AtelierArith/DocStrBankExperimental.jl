```
balancedaccuracy(tn::T, fp::T, fn::T, tp::T) where {T<:Integer}
```

The arithmetic mean of sensitivity and specificity, its use case is when dealing with imbalanced data

# Arguments

  * `tn::Integer` True negatives
  * `fp::Integer` False postives
  * `fn::Integer` False negatives
  * `tp::Integer` True positives
