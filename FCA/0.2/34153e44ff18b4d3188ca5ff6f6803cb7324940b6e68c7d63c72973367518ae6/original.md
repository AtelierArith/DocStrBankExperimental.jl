grad*neg*abs*sum*kurt(W, Z)

This function calcualtes the gradient of neg*abs*sum_kurt(W'*Z) w.r.t W

# Arguments

  * `W`: a matrix such that size(W, 1) = size(Z, 1)
  * `Z`: an array of vectors of the same length, regarded as the      realizations of mixed independent signals

# Outputs

  * `grad`: the gradient of neg*abs*sum_kurt(W'*Z) w.r.t W
