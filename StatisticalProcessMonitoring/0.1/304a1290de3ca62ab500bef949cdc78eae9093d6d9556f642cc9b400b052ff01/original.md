```
get_removable_terms(rhs)
```

Given an iterable collection of terms `rhs`, this function returns the indices of the terms in `rhs` that can be removed in a backward elimination step.

# Arguments

  * `rhs`: An iterable collection of terms in the equation.

# Returns

  * An array of indices of the terms in `rhs` that have the maximum order.
