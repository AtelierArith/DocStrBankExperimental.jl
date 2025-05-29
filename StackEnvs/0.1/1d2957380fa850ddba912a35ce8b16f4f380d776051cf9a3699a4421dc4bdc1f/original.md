```
update_env(env::StackEnv)
```

Add all packages in `env.packages` to the shared environment `env.name`.

If the shared environment `env.name` does not exist, it is created.

This is the same as [`create_env`](@ref) except no check is made that the environment does not already exist. Any packages that have already been added to the environment will be added again, which should be little more than a no-op.

# Examples

Say I want to add `CondaPkg.jl` to the packages in `env::StackEnv`.

```julia-repl
julia> env.packages
2-element Vector{Symbol}:
 :PythonCall
 :StatsBase

julia> push!(env, :CondaPkg)
3-element Vector{Symbol}:
 :PythonCall
 :StatsBase
 :CondaPkg

julia> update_env(env)
  Activating project at `~/.julia/environments/qkruntime_extra`
  ...
  Updating `~/.julia/environments/qkruntime_extra/Project.toml`
 [992eb4ea] + CondaPkg v0.2.24
```
