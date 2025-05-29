```
ensure_in_stack(env_name::AbstractString, env_packages::AbstractVector)::StackEnv
```

Create `env = StackEnv(env_name, env_packages)`, run `ensure_in_stack(env)` and return `env`.

Elements of `env_packages` should be `AbstractString`s or `Symbol`s.

See [`StackEnv`](@ref).

# Examples

```julia-repl
julia> ensure_in_stack("my_extra_env", [:PackageA, :PackageB]);
```
