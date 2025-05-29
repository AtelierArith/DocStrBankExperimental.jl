```
delete_from_stack!(env_name::Union{AbstractString, Symbol})
```

Delete environment `env_name` if and wherever it occurs in the stack `Base.LOAD_PATH`.

See [`StackEnv`](@ref).
