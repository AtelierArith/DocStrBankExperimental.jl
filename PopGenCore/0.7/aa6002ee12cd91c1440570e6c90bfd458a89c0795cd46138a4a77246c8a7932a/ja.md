```
sampleinfo!(::PopData, metadata::Pair{Symbol, Vector}; categorical::Bool = false)
sampleinfo!(::PopData, metadata::Pair{String, Vector}; categorical::Bool = false)
```

`PopData` メタデータに追加のサンプル情報を追加します。`PopData` をその場で変更します。メタデータは `sampleinfo(popdata)` のサンプルと同じ順序でなければなりません。

#### 引数

  * `metadata` : A Pair of :ColumnName => [Values]

#### キーワード引数

  * `categorical` : 追加されるメタデータがカテゴリカル（すなわち「因子」）であるかどうかのブール値（デフォルト: `false`）

## 例

```julia
cats = @nancycats
sampleinfo!(cats, :whiskerlength => rand(cats.metadata.samples))
sampleinfo!(cats, "tailcolor" => rand(["orange", "brown"], metadata(cats).samples), categorical = true)
cats
PopData{Diploid, 9 Microsatellite loci}
  Samples: 237
  Populations: 17
  Other Info: ["whiskerlength", "tailcolor"]
```
