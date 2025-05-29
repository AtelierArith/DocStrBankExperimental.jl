```
f1(; <keyword arguments>)
```

Assess performance of the classification model using F1-score. F1-score value ranges from 0 to 1.

# Arguments

  * `tp::Int64`: number of true positives
  * `tn::Int64`: number of true negatives
  * `fp::Int64`: number of false positives
  * `fn::Int64`: number of false negatives

# Returns

Named tuple containing:

  * `f1::Float64`: F1-score
  * `p::Float64`: precision
  * `r::Float64`: recall

# Source

https://www.statology.org/what-is-a-good-f1-score/
