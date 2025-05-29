```
higher_partial_moment(returns, threshold, n, method)
```

This function calculates the Higher Partial Moment (HPM) for a given threshold.

# Arguments

  * `returns`:     Vector of asset returns.
  * `threshold`:   Scalar value or vector denoting the threshold returns.
  * `n`:           `n`-th moment to calculate.
  * `method`:      One of `:full` or `:partial`. Indicates whether to use the number of all returns (`:full`), or only the number of returns above the threshold (`:partial`) in the denominator.

# Formula

$\text{HPM}_n = \frac{1}{D} \sum_{i=1}^N \max(0, \text{returns}_i - \text{threshold})^n$

where `N` is the number of returns, and `D` is the denominator.
