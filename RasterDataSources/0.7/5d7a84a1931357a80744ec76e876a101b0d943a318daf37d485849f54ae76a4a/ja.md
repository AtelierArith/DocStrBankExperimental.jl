```
getraster(T::Type{EarthEnv{LandCover}}, [layer]; discover=false) => Union{Tuple,String}
```

[`EarthEnv`](@ref) の土地被覆データをダウンロードします。

# 引数

  * `layer`: `(1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12)` からの `Integer` またはタプル/範囲、または `(:needleleaf_trees, :evergreen_broadleaf_trees, :deciduous_broadleaf_trees, :other_trees, :shrubs, :herbaceous, :cultivated_and_managed, :regularly_flooded, :urban_builtup, :snow_ice, :barren, :open_water)` からの `Symbol`。`layer` 引数がない場合、すべてのレイヤーがダウンロードされ、パスの `NamedTuple` が返されます。

# キーワード

  * `discover::Bool`: DISCover モデルを統合したデータセットをダウンロードするかどうか。

ダウンロードされたファイルまたは既存のファイルのファイルパスを返します。
