```
is_in_stack(env_name::AbstractString)::Bool
```

Return `true` if the shared environment `env_name` is in the environment stack.

If `env_name` does not start with `'@'`, it is prepended. The stack is `Base.LOAD_PATH`.
