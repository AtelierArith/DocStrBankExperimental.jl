```
confounders(o::CausalTable, x::Symbol, y::Symbol)
```

Selects the common causes for a specific pair of variables (x,y) from the given `CausalTable` object.

# Arguments

  * `o::CausalTable`: The `CausalTable` object from which to extract the confounders.
  * `x::Symbol`, `y::Symbol`: The two variables whose confounders should be selected.

# Returns

A new `CausalTable` containing only the confounders of both x and y.
