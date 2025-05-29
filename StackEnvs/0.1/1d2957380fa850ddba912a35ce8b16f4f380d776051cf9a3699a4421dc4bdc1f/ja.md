```
update_env(env::StackEnv)
```

`env.packages`にあるすべてのパッケージを共有環境`env.name`に追加します。

共有環境`env.name`が存在しない場合は、作成されます。

これは[`create_env`](@ref)と同じですが、環境がすでに存在しないかどうかのチェックは行われません。すでに環境に追加されているパッケージは再度追加されますが、これはほとんど何もしないのと同じです。

# 例

`env::StackEnv`のパッケージに`CondaPkg.jl`を追加したいとします。

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
