```
responseparents(o::CausalTable)
```

Selects the parents of each response variable from the given `CausalTable` object.

# Arguments

  * `o::CausalTable`: The `CausalTable` object from which to extract the parent variables of each response.
  * `collape_parents::Bool`: Optional parameter, whether to collapse the output to a single `CausalTable` object if there is either only one response or all response have the same parents. Defaults to `true`.

# Returns

A new `CausalTable` containing only the causes of the responses (if a single response, or all responses share the same set of causes); otherwise, a Vector of CausalTable objects containing the causes of each response.
