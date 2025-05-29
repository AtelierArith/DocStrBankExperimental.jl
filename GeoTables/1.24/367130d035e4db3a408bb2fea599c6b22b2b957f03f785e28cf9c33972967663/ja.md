```
geojoin(geotable₁, geotable₂, var₁ => agg₁, ..., varₙ => aggₙ; kind=:left, pred=intersects, on=nothing)
```

`geotable₁`を`geotable₂`と特定の`kind`の結合と、2つのジオメトリを受け取りブール値を返す述語関数`pred`を使用して結合します（`(g1, g2) -> g1 ⊆ g2`）。

オプションで、`on`キーワード引数に単一の名前または変数名のリスト（文字列またはシンボル）を渡すことで、ジオメトリの一致に加えて変数値の一致を追加できます。変数値の一致には`isequal`関数が使用されます。

2つ以上の一致が見つかった場合、`varᵢ`を集約関数`aggᵢ`で集約します。変数に対して集約関数が提供されていない場合、集約関数は科学的な型に応じて選択されます：連続の場合は`mean`、それ以外の場合は`first`です。

## 種類

  * `:left` - `geotable₁`のすべての行を返し、`geotable₂`に一致がない場合は`missing`でエントリを埋めます。
  * `:inner` - `geotable₂`に一致がある`geotable₁`の行のサブセットを返します。

# 例

```julia
geojoin(gtb1, gtb2)
geojoin(gtb1, gtb2, 1 => mean)
geojoin(gtb1, gtb2, :a => mean, :b => std)
geojoin(gtb1, gtb2, "a" => mean, pred=issubset)
geojoin(gtb1, gtb2, on=:a)
geojoin(gtb1, gtb2, kind=:inner, on=["a", "b"])
```

[`tablejoin`](@ref)も参照してください。
