```
update_env(env_name::AbstractString, env_packages::AbstractVector)::StackEnv
```

`env = StackEnv(env_name, env_packages)`を作成し、環境`env_name`を作成または更新します。

共有環境`env_name`は存在しない場合に作成されます。環境内に既存のパッケージは削除されません。`env_packages`内のパッケージがすでに環境に存在する場合、それらは再度追加されます。

`env_packages`の要素は`AbstractString`または`Symbol`である必要があります。

`update_env`は`create_env(env_name, env_packages)`と同じですが、後者は環境がすでに存在する場合にエラーをスローします。

[`StackEnv`](@ref)を参照してください。
