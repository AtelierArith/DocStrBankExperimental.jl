```
(tc::TypedCallable{A,R})(args...; kwargs...)
```

1. Enforces `args isa A`
2. Calls `tc.f` with the provided positional and keyword arguments
3. Enforces the return type of the above call as `R`
