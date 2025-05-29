```
run_sr(source_emis::DataFrame, [cell_variables]) -> receptor_emis::DataFrame
```

指定されたソース排出量に対してソース受容体マトリックスを実行します。各行は排出者を表します。`source_emis`は以下の列を持っている必要があります：

  * `latitude <: Number` - ソースの緯度
  * `longitude <: Number` - ソースの経度
  * `layer_idx <: Integer` - 層インデックス ∈ {1,2,3}、地上レベルでの有効排出高度（排出量が0〜57 m）、低レベル（57〜379 m）、および高レベル（>379 m）それぞれに対応
  * `<emis_type> <: Number` - 排出タイプ`<emis_type>` ∈ `{PM2_5, NOx, SO2, VOC, NH3}`の平均排出率、単位はμg / s。これらの列は1から5の間で存在することができます。
  * （オプション）`source_idx <: Int64` - ソースに対応するグリッドセルインデックス。指定された場合、`latitude`と`longitude`は使用されなくなります。

`receptor_emis`テーブルを返します。このテーブルには、ソース排出量によって生成された各PMタイプの列、`cell_variables`内の各変数の列、および各グリッドセルの`(lon, lat)`ジオメトリを含む`geometry_longlat`の列が含まれています。
