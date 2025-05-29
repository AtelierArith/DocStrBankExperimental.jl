```
gadm(country, subregions...; children=false, names=false, children_raw=false, reportlevels=false)
```

要求された国または国のサブリージョンのGMTdatasetを返します。

  * `country`: ISO 3166 Alpha 3 国コード 。
  * `subregions`: 階層順の完全な公式名（州、地区など）。 親のすべての行政子の名前を知るには、オプション `names` を使用します。
  * `children`: true の場合、関数は親のすべてのサブリージョンを返します。
  * `children_raw`: true の場合、関数は2つの変数 -> 親、子を返します。ここで、子は GDAL オブジェクトです。たとえば、children が true に設定され、国のみをクエリすると、2番目の返されるパラメータは州/省です。`children` の場合、ポリゴンを持つ GMTdataset のベクターを返します。`children_raw` の場合、2番目の出力は GADM.jl のような GDAL オブジェクトです（Tables.jl を除く）。
  * `names`: すべての `children` の名前を含む文字列ベクターを返します。
  * `reportlevels`: 行政レベルの数（国を含む）を報告し、終了します。

## 例

```julia
# インドの国境のデータ
data = gadm("IND")

# uttar -> ウッタル・プラデーシュ州の境界
uttar = gadm("IND", "Uttar Pradesh")

# uttar -> ウッタル・プラデーシュ州のすべての地区の境界
uttar = gadm("IND", "Uttar Pradesh", children=true)

# インドのすべての州の名前
gadm("IND", names=true)
```
