```
test_patterns(patterns::Vector{Union{String,Regex}})::Nothing
```

Specify patterns for the tests to run. Only tests whose full `test_name` matches one of the patterns will be run. If the vector is empty, all tests will be run.
