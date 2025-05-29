```
parents(o::CausalTable, symbol)
```

Selects the variables that precede `symbol` causally from the CausalTable `o`, based on the `causes` attribute. Note that if `symbol` is not contained within `o.causes`, this function will output an empty `CausalTable`.

# Arguments

  * `o::CausalTable`: The `CausalTable` object from which to extract the parent variables of `symbol`.
  * `symbol`: The variable for which to extract the parent variables.

# Returns

A new `CausalTable` containing only the parents of `symbol`
