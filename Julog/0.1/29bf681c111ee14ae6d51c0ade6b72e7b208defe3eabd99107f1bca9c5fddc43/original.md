```
unify(src, dst[, occurs_check, funcs])
```

Unifies src with dst and returns a dictionary of any substitutions needed.

# Arguments

  * `src::Term`: A term to unify.
  * `dst::Term`: A term to unify (src/dst order does not matter).
  * `occurs_check::Bool=true`: Whether to perform the occurs check.
  * `funcs::Dict=Dict()`: Custom functions to evaluate.
