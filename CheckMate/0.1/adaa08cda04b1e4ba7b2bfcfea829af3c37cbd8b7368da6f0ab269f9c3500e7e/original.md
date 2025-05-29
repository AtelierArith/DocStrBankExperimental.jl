```
passed_checks(summary::CheckSummary)::Vector{String}
```

Retrieve the names of all checks that passed successfully.

# Arguments

  * `summary::CheckSummary`: A summary object containing the results of multiple checks.

# Returns

A vector of check names that passed.

# Examples

```julia
checks = passed_checks(summary)  # Returns ['check3', 'check4', ...]
```
