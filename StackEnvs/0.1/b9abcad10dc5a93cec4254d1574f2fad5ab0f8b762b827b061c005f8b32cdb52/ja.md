```
ensure_in_stack(env_name::AbstractString, env_packages::AbstractVector)::StackEnv
```

`env = StackEnv(env_name, env_packages)`を作成し、`ensure_in_stack(env)`を実行して`env`を返します。

`env_packages`の要素は`AbstractString`または`Symbol`である必要があります。

[`StackEnv`](@ref)を参照してください。

# 例

```julia-repl
julia> ensure_in_stack("my_extra_env", [:PackageA, :PackageB]);
```
