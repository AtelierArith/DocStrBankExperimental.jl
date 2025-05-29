```
@unwrap_error_or(expr, exec)
```

Evaluate `expr` to a `Result`. If `expr` is a result value, evaluate `exec` and return that. Else, return the wrapped error value in `expr`.

See also: [`@unwrap_or`](@ref) ```
