```
failing_rows(summary::CheckSummary)::Vector{Int}
```

Retrieve all unique failing row indices across all checks.

# Arguments

  * `summary::CheckSummary`: A summary object containing the results of multiple checks.

# Returns

A sorted vector of unique row indices that failed any check.

# Examples

```julia
all_failed_indices = failing_rows(summary)  # Returns [1, 2, 5, 8, ...]
```
