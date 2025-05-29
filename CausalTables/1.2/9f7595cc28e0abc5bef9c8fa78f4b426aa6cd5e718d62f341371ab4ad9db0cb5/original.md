```
reject(o::CausalTable, symbols)
```

Removes the columns specified by `symbols` from the `CausalTable` object `o`.

# Arguments

  * `o::CausalTable`: The `CausalTable` object from which symbols will be rejected.
  * `symbols`: A collection of symbols to be rejected from the `CausalTable`.

# Returns

A new `CausalTable` object with the specified symbols removed from its data.
