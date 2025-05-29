```
autocovariance(g⃗, Q::Eigen, timelist; progress=false)
```

Calculate the autocovariance of observable g⃗ with generator matrix Q and times at timelist. 

# Arguments

  * `g⃗::AbstractVector`: observable
  * `Q::Eigen`: eigenvalue decomposition of generator matrix
  * `timelist::AbstractVector`: times at which to calculate autocovariance

# Keyword Arguments

  * `progress::Bool=false`: show a progress bar

# Returns

  * `autocov::Vector`: autocovariance of observable g⃗ with generator matrix Q and times at timelist
