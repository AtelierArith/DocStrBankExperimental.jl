```
locusinfo!(::PopData, metadata::Pair{Symbol, Vector}; categorical::Bool = false)
locusinfo!(::PopData, metadata::Pair{String, Vector}; categorical::Bool = false)
```

`PopData` メタデータに追加のローカス情報を追加します。`PopData` をその場で変更します。メタデータは `locusinfo(PopData)` のサンプルと同じ順序でなければなりません。

#### 引数

  * `metadata` : :ColumnName => [Values] のペア

#### キーワード引数

  * `categorical` : 追加されるメタデータがカテゴリカル（いわゆる「因子」）であるかどうかのブール値（デフォルト: `false`）

## 例

```julia
cats = @nancycats
locusinfo!(cats, :quality => rand(metadata(cats).loci))
cats
PopData{Diploid, 9 Microsatellite loci}
  Samples: 237
  Populations: 17
  Other Info: ["quality"]
```
