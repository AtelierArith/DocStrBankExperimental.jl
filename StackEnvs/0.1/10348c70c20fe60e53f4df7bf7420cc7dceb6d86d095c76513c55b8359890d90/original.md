```
env_exists(env_name::AbstractString)::Bool
```

Return `true` if the shared environment `env_name` already exists.

`env_name` may begin with "@" or not.

This environment might be activated via `Pkg.activate(env_name)` If done from the `pkg` repl, the name must start with `'@'`.
