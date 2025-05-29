```
StackEnv(env_name::AbstractString)
```

空のパッケージリストで`StackEnv`を初期化します。

# 例

```jldoctest
julia> StackEnv("an_extra_env")
StackEnv("an_extra_env", Symbol[])

julia> StackEnv("@an_extra_env")
StackEnv("an_extra_env", Symbol[])
```
