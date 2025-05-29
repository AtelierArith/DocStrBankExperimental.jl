```julia
sysappscore(s::Santiago.System; α) -> Float64

```

Compute the system appropriateness score (SAS). `α` ∈ [0, 1] gradually changes from the arithmetic mean (α=0) to the  a geometric mean (`α=1`).
