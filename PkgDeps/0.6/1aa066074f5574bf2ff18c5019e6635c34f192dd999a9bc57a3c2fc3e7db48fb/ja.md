```
direct_dependencies(pkg_name::String;
    registries::Array{RegistryInstance}=reachable_registries()) -> Dict{String, UUID}
direct_dependencies(pkg_uuid::UUID; registries::Array{RegistryInstance}=reachable_registries()) -> Dict{String, UUID}
```

指定されたパッケージの最新バージョンの直接依存関係を、名前をキー、UUIDを値とする`Dict`の形式で返します。

標準ライブラリには依存関係がないと仮定されます。
