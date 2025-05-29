```
pass_rate(summary::CheckSummary)::Float64
```

Calculate the percentage of rows that passed all checks.

# Arguments

  * `summary::CheckSummary`: A summary object containing the results of multiple checks.

# Returns

Percentage of rows that passed all checks, rounded to one decimal place (0-100).

# Examples

```julia
rate = pass_rate(summary)  # Returns 95.0 if 95% of rows passed all checks
```
