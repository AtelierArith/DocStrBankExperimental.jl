```
failed_checks(summary::CheckSummary)::Vector{String}
```

Retrieve the names of all checks that did not pass.

# Arguments

  * `summary::CheckSummary`: A summary object containing the results of multiple checks.

# Returns

A vector of check names that failed (did not pass).

# Examples

```julia
checks = failed_checks(summary)  # Returns ['check1', 'check2', ...]
```
