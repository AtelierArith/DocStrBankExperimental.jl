```
tablejoin(geotable, table, var₁ => agg₁, ..., varₙ => aggₙ; kind=:left, on)
```

`geotable`を`table`と結合し、`on`変数の値を使用して特定の`kind`の結合で行を一致させます。

`on`変数は単一の名前または変数名のリスト（文字列またはシンボル）であることができます。変数値の一致には`isequal`関数が使用されます。

2つ以上の一致が見つかった場合、`varᵢ`を集約関数`aggᵢ`で集約します。変数に集約関数が提供されていない場合、集約関数は科学的型に応じて選択されます：連続の場合は`mean`、それ以外の場合は`first`です。

## 種類

  * `:left` - `geotable`のすべての行を返し、`table`に一致がない場合は`missing`でエントリを埋めます。
  * `:inner` - `table`に一致がある`geotable`の行のサブセットを返します。

# 例

```julia
tablejoin(gtb, tab, on=:a)
tablejoin(gtb, tab, 1 => mean, on=:a)
tablejoin(gtb, tab, :a => mean, :b => std, on=:a)
tablejoin(gtb, tab, "a" => mean, on=[:a, :b])
tablejoin(gtb, tab, kind=:inner, on=["a", "b"])
```

[`geojoin`](@ref)も参照してください。
