```
test_call(f, [types]; broken::Bool = false, skip::Bool = false, jetconfigs...)
test_call(tt::Type{<:Tuple}; broken::Bool = false, skip::Bool = false, jetconfigs...)
```

Runs [`report_call`](@ref) on a function call with the given type signature and tests that it is free from problems that `report_call` can detect. Except that it takes a type signature rather than a call expression, this function works in the same way as [`@test_call`](@ref).
