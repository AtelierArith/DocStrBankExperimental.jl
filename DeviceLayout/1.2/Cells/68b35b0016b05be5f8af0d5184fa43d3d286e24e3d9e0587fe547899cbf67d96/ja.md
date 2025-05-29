```
Cell(name::AbstractString)
```

`Cell{typeof(1.0UPREFERRED)}`の便利なコンストラクタです。

[`DeviceLayout.UPREFERRED`](@ref) は、`Project.toml` または `LocalPreferences.toml` の `unit` の設定に従って設定された定数です。デフォルト（`"PreferNanometers"`）は `const UPREFERRED = DeviceLayout.nm` を与え、混合単位の操作は `nm` への変換を優先します。

単位の好みは、GDS エクスポートのデータベーススケールには影響しません。
