```
test_prefixes(prefixes::Vector{Union{String}})::Nothing
```

Specify prefixes for the tests to run. Only tests whose [`test_name`](@ref) matches any of these prefixes will be run. If the vector is empty (the default), all the tests will be run.
