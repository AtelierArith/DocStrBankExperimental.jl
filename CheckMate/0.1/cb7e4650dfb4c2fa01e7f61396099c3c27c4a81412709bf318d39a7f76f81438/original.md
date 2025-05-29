```
failing_rows(summary::CheckSummary, check_name::String)::Vector{Int}
```

Retrieve the row indices that failed for a specific named check.

# Arguments

  * `summary::CheckSummary`: A summary object containing the results of multiple checks.
  * `check_name::String`: The name of the specific check to retrieve failing rows for.

# Returns

A vector of row indices that failed the specified check.

# Throws

  * `ErrorException` if the specified check name is not found in the summary.

# Examples

```julia
failed_indices = failing_rows(summary, "column_type_check")  # Returns [3, 7, 10, ...]
```
