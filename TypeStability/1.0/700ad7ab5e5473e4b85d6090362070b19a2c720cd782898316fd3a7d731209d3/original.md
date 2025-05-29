```
check_function(func, signatures, acceptable_instability=Dict())
```

Check that the function is stable under each of the given signatures.

Return an array of method signature-`StabilityReport` pairs from [`check_method`](@ref).
