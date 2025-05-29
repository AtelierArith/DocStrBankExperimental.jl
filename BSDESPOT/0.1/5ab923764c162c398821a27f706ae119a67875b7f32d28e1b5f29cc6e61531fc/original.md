```
IndependentBounds(lower, upper, check_terminal=false, consistency_fix_thresh=0.0)
```

Specify lower and upper bounds that are independent of each other (the most common case).

# Keyword Arguments

  * `check_terminal::Bool=false`: if true, then if all the states in the belief are terminal, the upper and lower bounds will be overridden and set to 0.
  * `consistency_fix_thresh::Float64=0.0`: if `upper < lower` and `upper >= lower-consistency_fix_thresh`, then `upper` will be bumped up to `lower`.
