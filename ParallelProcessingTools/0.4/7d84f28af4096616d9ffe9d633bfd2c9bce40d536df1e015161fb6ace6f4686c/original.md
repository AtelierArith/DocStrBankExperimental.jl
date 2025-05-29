```
@return_exceptions expr
```

Runs `expr` and catches and returns exceptions as values instead of having them thrown.

Useful for user-side debugging, especially of parallel and/or remote code execution.

See also [`@userfriendly_exceptions`](@ref).
