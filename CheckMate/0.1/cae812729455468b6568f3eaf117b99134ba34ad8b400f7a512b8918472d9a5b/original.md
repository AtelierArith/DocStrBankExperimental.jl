```
failing_rows(result::CheckResult)::Vector{Int}
```

Retrieve the row indices that failed for a specific check result.

# Arguments

  * `result::CheckResult`: A result object for a single check.

# Returns

A vector of row indices that failed the check.

# Examples

```julia
failed_indices = failing_rows(result)  # Returns [2, 5, 8, ...]
```
