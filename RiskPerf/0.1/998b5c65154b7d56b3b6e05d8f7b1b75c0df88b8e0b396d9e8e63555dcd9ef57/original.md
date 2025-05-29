```
upside_deviation(returns, threshold; method=:full)
```

Calculates the upside deviation, also called semi-standard deviation, which captures the upside "risk".

# Arguments

  * `returns`:     Vector of asset returns.
  * `threshold`:   Scalar value or vector denoting the threshold returns.
  * `method`:      One of `:full` (default) or `:partial`. Indicates whether to use the number of all returns (`:full`), or only the number of returns above the threshold (`:partial`) in the denominator.

# Formula

$\text{Upside Deviation} = \sqrt{\text{Higher Partial Moment}}$
