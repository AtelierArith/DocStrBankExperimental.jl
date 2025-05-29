```
pass_rate(summary::CheckSummary, check_name::String)::Float64
```

Calculate the pass rate for a specific check based on number of rows that passed.

# Arguments

  * `summary::CheckSummary`: A summary object containing the results of multiple checks.
  * `check_name::String`: The name of the specific check to calculate pass rate for.

# Returns

Percentage of rows that passed the specified check, rounded to one decimal place (0-100).

# Examples

```julia
rate = pass_rate(summary, "column_type_check")  # Returns 95.0 if 95% of rows passed this check
```
