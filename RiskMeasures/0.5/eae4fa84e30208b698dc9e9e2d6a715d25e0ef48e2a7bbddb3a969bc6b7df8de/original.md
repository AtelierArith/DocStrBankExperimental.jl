```
VaR(values, pmf, α; ...)
```

Compute VaR for a discrete random variable with `values` and the probability mass function `pmf`.  Also compute the index that achieves the value at risk. 

If `α = 0`, VaR returns the essential infimum, and if `α = 1`, VaR returns maximum possible value, becuase VaR_1 is infinity.

Runs in $n \log(n)$ time where `n = length(x̃)`.

# Returns

A named tuple with VaR `value` and the `index` that achieves it. If such an index does not exist, then returns -1.

# Keyword Arguments:

  * `check_inputs=true`: check that the inputs are valid.
  * `fast=false`: use linear-time experimental implementation
