```
Survey(table; [holeid], [at], [azm], [dip])
```

調査 `table` は、指定された `holeid` に沿った掘削孔の各深さ（通常はメートル）での `azm` および `dip` 角度（通常は度）を格納します。

キーワード引数が省略された場合、一般的な列名が `table` 内で検索されます。

## 例

```julia
Survey(table, holeid="BHID", at="DEPTH")
Survey(table, azm="AZIMUTH")
```

関連情報は [`Collar`](@ref)、[`Interval`](@ref) を参照してください。
