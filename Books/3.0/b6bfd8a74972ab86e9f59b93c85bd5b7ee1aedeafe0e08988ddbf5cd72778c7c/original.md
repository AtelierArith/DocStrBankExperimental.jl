```
@sco(f::Function, types;
    process::Union{Nothing,Function}=nothing, post::Function=identity)
```

Show code and output for `f()`; to show only code, use [`@sc`](@ref). See [`sco`](@ref) for more information about `process` and `post`.
