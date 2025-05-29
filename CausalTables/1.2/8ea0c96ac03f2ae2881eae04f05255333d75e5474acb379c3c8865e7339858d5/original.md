```
confounders(o::CausalTable; collapse_parents = true)
```

Selects the confounders of each response-treatment pair from the given `CausalTable` object.

# Arguments

  * `o::CausalTable`: The `CausalTable` object from which to extract the confounder variables of each treatment-response pair.
  * `collape_parents::Bool`: Optional parameter, whether to collapse the output to a single `CausalTable` object if there is either only one treatment-response pair or all pair share the same set of confounders. Defaults to `true`.

# Returns

A new `CausalTable` containing only the confounders (if a single response, or all responses share the same set of causes); otherwise, a Matrix of CausalTable objects containing the confounders of each treatment-response pair, where rows represent responses and columns represent treatments.
