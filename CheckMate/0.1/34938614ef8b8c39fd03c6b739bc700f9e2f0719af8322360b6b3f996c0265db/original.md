```
execution_time(summary::CheckSummary)::Float64
```

Retrieve the total execution time of all checks.

# Arguments

  * `summary::CheckSummary`: A summary object containing the results of multiple checks.

# Returns

Total execution time in seconds.

# Examples

```julia
time = execution_time(summary)  # Returns execution time in seconds
```
