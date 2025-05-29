```
struct StackEnv
```

Data for defining a shared environment to be used in the environment stack.

When working with a particular package, you might frequently use certain other packages that are not in the dependencies of the particular one. `StackEnv` is meant to help manage these other packages. You can do this by hand as well. But it's sometimes not easy to remember what you want to do and exactly how to do it.

`StackEnv` helps you create a shared environment and make sure it is in your stack of environments so that its packages are visibile when it is not the active environment. You are *not* meant to do work with the environment in `StackEnv` activated.

The most important function for creating an `StackEnv` and making it visible is [`ensure_in_stack`](@ref).

# Fields

  * `name::String`: the name of the extra environment
  * `packages::Vector{Symbol}`: A list of packages to use to initialize the environment.

See [`update_env`](@ref) [`create_env`](@ref), [`ensure_in_stack`](@ref), [`env_exists`](@ref), [`activate_env`](@ref), [`is_in_stack`](@ref), [`delete_from_stack!`](@ref).

# Examples

```jldoctest
julia> StackEnv("an_extra_env", [:Example])
StackEnv("an_extra_env", [:Example])

julia> StackEnv("@an_extra_env", [:Example])
StackEnv("an_extra_env", [:Example])
```
