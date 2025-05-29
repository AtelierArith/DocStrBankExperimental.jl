```
mediatornames(o::CausalTable, x::Symbol, y::Symbol)
```

Outputs the names of the mediators of the causal relationship between `x` and `y` from the given `CausalTable` object.

# Arguments

  * `o::CausalTable`: The `CausalTable` object from which to extract the mediator names.
  * `x::Symbol`, `y::Symbol`: The two variables whose mediators should be selected.

# Returns

A Vector of Symbols containing the names of the mediators between x and y.
