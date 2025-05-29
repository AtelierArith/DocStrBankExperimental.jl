```
get_path()
```

指定されたアセットタイプのパスを取得します。

# 引数

  * `asset_type::Symbol`: アセットのタイプ。可能な値は `:examples`、`：addons`、および `:templates` です。

# 戻り値

  * `String`: 指定されたタイプのすべてのアセットを含むフォルダーのパス。

# 例

```julia
get_path(:examples)
```
