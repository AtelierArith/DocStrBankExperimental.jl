```
mscr(; <keyword arguments>)
```

Assess performance of the classification model using misclassification rate.

# Arguments

  * `tp::Int64`: number of true positives
  * `tn::Int64`: number of true negatives
  * `fp::Int64`: number of false positives
  * `fn::Int64`: number of false negatives

# Returns

Named tuple containing:

  * `mr::Float64`: misclassification rate
  * `acc::Float64`: accuracy

# Source

https://www.statology.org/misclassification-rate/
