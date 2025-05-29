```
@critical expr
```

Terminates the testcase on failure of an assertion `expr`. `expr` must start from one of [`@test`](@ref), [`@test_fail`](@ref), [`@test_throws`](@ref), [`@test_broken`](@ref), [`@inferred`](@ref), [`@test_warn`](@ref), [`@test_nowarn`](@ref).
