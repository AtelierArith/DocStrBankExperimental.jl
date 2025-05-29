```
categorical_to_index(g::AbstractVector, table::AbstractMatrix)
```

Converts a categorized variable `g` to its corresponding index in a table.

# Arguments

  * `g::AbstractVector`: The categorical variable to convert.
  * `table::AbstractMatrix`: The table containing all the possible categories.

# Returns

  * `Int`: The index of the category in the table.

# Raises

  * `ErrorException` if the index is not found

# Example

```
x = randn(500, 3)
df, table, qtls = create_table(x, [2 for _ in eachcol(x)])
xnew = randn(3)
g = categorize_data(xnew, qtls)
idx = categorical_to_index(g, table)
```
