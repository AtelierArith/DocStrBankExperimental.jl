```
dependencies(
    pkg_name::Union{AbstractString, Missing}, pkg_uuid::Union{Missing, UUID}=missing;
    registries::Array{RegistryInstance}=reachable_registries()
)
```

`pkg_name`の最新バージョンが依存しているすべてのパッケージを見つけます（直接的または間接的に）。

注意: 依存関係ツリー内の各パッケージは最新バージョンであると仮定されます。互換性の制約は無視されます。さらに、標準ライブラリは依存関係を持たないと仮定されます。

# 引数

  * `pkg_name::AbstractString`: パッケージの名前
  * `pkg_uuid::UUID`: パッケージのUUID（利用可能な場合）

# キーワード

  * `registries::Array{RegistryInstance}=reachable_registries()`: 調査するレジストリ

# 戻り値

  * `Dict{String, UUID}()`: `pkg_name`が依存しているパッケージ。
