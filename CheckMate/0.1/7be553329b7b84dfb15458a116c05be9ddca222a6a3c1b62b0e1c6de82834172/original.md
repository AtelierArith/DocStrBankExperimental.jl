```
check_names(checkset::CheckSet)::Vector{String}
```

Retrieve the names of all checks in a given checkset.

# Arguments

  * `checkset::CheckSet`: A checkset object.

# Returns

A vector of check names in the specified checkset.

# Examples

```julia
names = check_names(checkset)  # Returns ["check1", "check2", ...]
```
