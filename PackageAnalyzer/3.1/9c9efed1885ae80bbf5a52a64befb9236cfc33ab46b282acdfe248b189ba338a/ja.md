```
find_packages_in_manifest([path_to_manifest]; registries=reachable_registries(),
                          strict=true, warn=true)) -> Vector{PkgSource}
```

`Manifest.toml`に保存されているすべてのパッケージ/バージョンの組み合わせに関連付けられた`Vector{PkgSource}`を返します。

  * `path_to_manifest`はデフォルトで`joinpath(dirname(Base.active_project()), "Manifest.toml")`になります。
  * registries: 探索する`RegistryInstance`のコレクション
  * `strict`と`warn`は[`find_package`](@ref)と同じ意味を持ちます。
  * 標準ライブラリは常にスキップされ、警告やエラーは表示されません。
