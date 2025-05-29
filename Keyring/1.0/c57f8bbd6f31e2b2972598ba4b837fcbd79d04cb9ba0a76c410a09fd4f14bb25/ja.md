```
get_credential(target::AbstractString)
get_credential(store::AbstractCredentialStore, target::AbstractString)
```

見つからない場合は、[Credential](@ref) または `Some(nothing)` を返します。

指定されていない場合、`store` は [`DEFAULT_CREDENTIAL_STORE`](@ref) の値にデフォルト設定されます。

# 例

```julia_repl
julia> set_credential("my_target", "my_username", "my_secret")
julia> c = get_credential("my_target")
```
