```
get_longterm_temps(rgi_id::String, params::Parameters, climate::RasterStack) -> Array{Float64}
```

指定された氷河の長期平均気温を計算します。

# 引数

  * `rgi_id::String`: 氷河のためのRGI（Randolph Glacier Inventory）識別子。
  * `params::Parameters`: RGIデータへのパスを含むシミュレーションパラメータを含む構造体。
  * `climate::RasterStack`: 気候データを含む`RasterStack`オブジェクト。

# 戻り値

  * `Array{Float64}`: 長期平均気温の配列。

# 説明

この関数は、指定された氷河のRGI識別子を使用してグリッドデータを取得します。次に、氷河の地形に基づいて気候データに温度勾配を適用します。最後に、温度データを年ごとにグループ化し、各グループの平均を計算することによって長期平均気温を算出します。
