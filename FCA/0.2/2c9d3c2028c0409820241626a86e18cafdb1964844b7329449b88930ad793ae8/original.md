```
grad_neg_abs_sum_free_kurt(W, Y)
```

This function calcualtes the gradient of neg*abs*sum*free*kurt(W'*Y) w.r.t W

# Arguments

  * `W`: a matrix such that size(`W`, 1) = size(`Y`, 1)
  * `Y`: an array of matrix of same type and same dimension

# Outputs

  * `grad`: the gradient of neg*abs*sum*free*kurt(W'*Y) w.r.t W
