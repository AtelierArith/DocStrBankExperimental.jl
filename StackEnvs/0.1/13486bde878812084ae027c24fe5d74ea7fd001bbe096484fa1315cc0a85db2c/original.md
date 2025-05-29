```
StackEnv(env_name::AbstractString)
```

Initialize an `StackEnv` with an empty list of packages.

# Examples

```jldoctest
julia> StackEnv("an_extra_env")
StackEnv("an_extra_env", Symbol[])

julia> StackEnv("@an_extra_env")
StackEnv("an_extra_env", Symbol[])
```
