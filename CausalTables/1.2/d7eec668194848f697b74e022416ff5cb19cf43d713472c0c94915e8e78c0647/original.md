```
select(o::CausalTable, symbols)
```

Selects specified columns from a `CausalTable` object.

# Arguments

  * `o::CausalTable`: The `CausalTable` object from which columns are to be selected.
  * `symbols`: A list of symbols representing the columns to be selected.

# Returns

  * A new `CausalTable` object with only the selected columns.
