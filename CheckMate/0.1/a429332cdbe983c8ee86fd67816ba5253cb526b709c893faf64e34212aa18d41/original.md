```
check_columns(checkset::CheckSet, check_name::String)::Vector{Symbol}
```

Retrieve the column names for a specific named check.

# Arguments

  * `checkset::CheckSet`: A checkset object.
  * `check_name::String`: The name of the specific check to retrieve column names for.

# Returns

A vector of column names used in the specified check.

# Examples

```julia
columns = check_columns(checkset, "column_type_check")  # Returns [:a, :b]
```
