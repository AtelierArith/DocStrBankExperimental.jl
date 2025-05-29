```
update_env(env_name::AbstractString, env_packages::AbstractVector)::StackEnv
```

Create `env = StackEnv(env_name, env_packages)` and create or update the environment `env_name`.

The shared environment `env_name` will be created if it does not exist. Possible existing packages in the the environment are not removed. If packages in `env_packages` are already in the environment, they are added again.

Elements of `env_packages` should be `AbstractString`s or `Symbol`s.

`update_env` is the same as `create_env(env_name, env_packages)` except that the latter will throw an error if the environment already exists.

See [`StackEnv`](@ref).
