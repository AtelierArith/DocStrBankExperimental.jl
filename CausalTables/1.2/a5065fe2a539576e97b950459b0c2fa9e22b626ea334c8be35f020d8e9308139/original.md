```
mediators(o::CausalTable, x::Symbol, y::Symbol)
```

Selects the mediators for a specific pair of variables (x,y) from the given `CausalTable` object; that is, the variables that are caused by x and cause y.

# Arguments

  * `o::CausalTable`: The `CausalTable` object from which to extract the mediators.
  * `x::Symbol`, `y::Symbol`: The two variables whose mediators should be selected.

# Returns

A new `CausalTable` containing only the mediators of both x and y.
