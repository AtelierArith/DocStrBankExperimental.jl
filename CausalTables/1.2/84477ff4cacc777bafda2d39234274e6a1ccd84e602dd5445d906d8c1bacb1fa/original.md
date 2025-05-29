```
instruments(o::CausalTable; collapse_parents = true)
```

Selects the instruments of each treatment-response pair from the given `CausalTable` object; that is, variables that are associated with the treatment but do not cause the response.

# Arguments

  * `o::CausalTable`: The `CausalTable` object from which to extract the instrumental variables of each treatment-response pair.
  * `collape_parents::Bool`: Optional parameter, whether to collapse the output to a single `CausalTable` object if there is either only one treatment-response pair or all pair share the same set of instruments. Defaults to `true`.

# Returns

A new `CausalTable` containing only the instruments (if a single response, or all responses share the same set of instruments); otherwise, a Matrix of CausalTable objects containing the instruments of each treatment-response pair, where rows represent responses and columns represent treatments.
