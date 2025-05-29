```
grad_sum_free_ent(W, Z; mat = "her")
```

This function calcualtes the gradient of sum*free*ent(W'*Y) w.r.t W

# Arguments

  * `W`: a matrix such that size(W, 1) = size(Y, 1)
  * `Y`: an array of matrix of same type and same dimension

# Outputs

  * `grad`: the gradient of sum*free*ent(W'*Y) w.r.t W
