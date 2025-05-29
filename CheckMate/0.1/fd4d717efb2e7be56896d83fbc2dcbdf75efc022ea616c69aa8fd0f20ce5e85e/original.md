```
total_failures(summary::CheckSummary)::Int
```

Calculate the total number of failing rows across all checks.

# Arguments

  * `summary::CheckSummary`: A summary object containing the results of multiple checks.

# Returns

Total count of rows that failed validation across all checks.

# Examples

```julia
total_failed = total_failures(summary)  # Returns the total number of failing rows
```
