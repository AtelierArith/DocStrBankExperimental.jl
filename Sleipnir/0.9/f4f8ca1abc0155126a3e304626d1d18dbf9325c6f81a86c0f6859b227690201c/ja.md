```
get_longterm_temps(rgi_id::String, params::Parameters)
```

指定された氷河の長期平均気温を計算します。

# 引数

  * `rgi_id::String`: 氷河のためのRGI（Randolph Glacier Inventory）識別子。
  * `params::Parameters`: 必要なデータファイルへのパスを含むシミュレーションパラメータを持つ`Parameters`オブジェクト。

# 戻り値

  * `longterm_temps`: 氷河の長期平均気温のベクトル。

# 説明

この関数は、指定された氷河のグリッドデータと生の気候データを読み込み、氷河の地形に基づいて温度勾配補正を適用し、次に温度データを年ごとにグループ化して長期平均気温を計算します。
