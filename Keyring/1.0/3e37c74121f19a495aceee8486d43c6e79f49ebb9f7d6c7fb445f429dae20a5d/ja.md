```
set_credential(target::AbstractString, username::AbstractString, secret::AbstractString)
set_credential(store::AbstractCredentialStore, target::AbstractString, username::AbstractString, secret::AbstractString)
```

値を設定し、`nothing`を返します。

指定されていない場合、`store`は[`DEFAULT_CREDENTIAL_STORE`](@ref)の値にデフォルト設定されます。
