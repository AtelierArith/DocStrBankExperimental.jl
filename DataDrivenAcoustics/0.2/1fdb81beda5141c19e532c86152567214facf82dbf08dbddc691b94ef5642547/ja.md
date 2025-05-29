```julia
SplitData(location, measurement, ratioₜ, seed)

```

位置と音響測定データをトレーニングデータセットと検証データセットに分割します。

  * `location`: 測定位置
  * `measurement`: 対応する音響測定値
  * `ratioₜ`: トレーニングデータの分割比率
  * データ分割のランダム順序生成にシードを設定するには、`seed`を`true`に設定します。
