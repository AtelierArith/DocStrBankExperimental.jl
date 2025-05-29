```
find_package(name_or_uuid::Union{AbstractString, UUID}; registries=reachable_registries(), version::Union{VersionNumber,Nothing}=nothing, strict=true, warn=true) -> PkgSource
```

パッケージ `pkg` の [`PkgSource`](@ref) を返します。

  * registries: 探索する `RegistryInstance` のコレクション
  * `version`: `nothing` の場合、任意のレジストリで最大の登録バージョンを見つけます。それ以外の場合は、そのバージョン番号を探します。
  * `strict` が true の場合、パッケージが見つからないとエラーになります。それ以外の場合は、`nothing` を返します。
  * `warn` が true の場合、パッケージが見つからないと警告します。

関連情報: [`find_packages`](@ref).
