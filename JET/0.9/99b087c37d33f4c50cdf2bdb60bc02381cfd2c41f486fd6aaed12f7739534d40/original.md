```
test_opt(f, [types]; broken::Bool = false, skip::Bool = false, jetconfigs...)
test_opt(tt::Type{<:Tuple}; broken::Bool = false, skip::Bool = false, jetconfigs...)
```

Runs [`report_opt`](@ref) on a function call with the given type signature and tests that it is free from optimization failures and unresolved method dispatches that `report_opt` can detect. Except that it takes a type signature rather than a call expression, this function works in the same way as [`@test_opt`](@ref).
