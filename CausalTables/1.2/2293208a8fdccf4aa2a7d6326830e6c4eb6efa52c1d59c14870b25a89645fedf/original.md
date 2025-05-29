```
mediators(o::CausalTable; collapse_parents = true)
```

Selects the mediators of each treatment-response pair from the given `CausalTable` object.

# Arguments

  * `o::CausalTable`: The `CausalTable` object from which to extract the mediator variables of each treatment-response pair.
  * `collape_parents::Bool`: Optional parameter, whether to collapse the output to a single `CausalTable` object if there is either only one treatment-response pair or all pair share the same set of mediators. Defaults to `true`.

# Returns

A new `CausalTable` containing only the mediators (if a single response, or all responses share the same set of mediators); otherwise, a Matrix of CausalTable objects containing the mediators of each treatment-response pair, where rows represent responses and columns represent treatments.
