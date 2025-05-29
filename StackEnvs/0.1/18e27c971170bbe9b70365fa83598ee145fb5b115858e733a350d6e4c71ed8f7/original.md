```
ensure_in_stack(env::StackEnv)::StackEnv
```

Ensure that a shared environment `env.name` with `env.packages` is in your stack.

Recall that the environment stack is `Base.LOAD_PATH`.

If `env.name` does not name a shared environment, create it and add `env.packages`. Furthermore, if `env.name` is not in the stack, add it to the stack.

After this runs, the packages `env.packages` should be available in whatever project is active.

`ensure_in_stack` compares `env.packages` to the list of packages in the `Project.toml` for the environment and adds any missing packages that you may have added since the environment was first created.

Things that are not supported:

  * removing packages from the environment for any reason.
  * Specifying or checking versions, uuids, etc.

The function [`update_env`](@ref) will unconditionally add all packages in `env.packages` to the environment, which may perform an upgrade (I'm not sure).

See [`StackEnv`](@ref).
