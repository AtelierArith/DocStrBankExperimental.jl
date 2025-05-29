```
RNADwellTimeData
```

RNA滞留時間データを格納するための構造体。

# フィールド

  * `label::String`: データセットのラベル。
  * `gene::String`: 遺伝子名（大文字と小文字を区別）。
  * `nRNA::Int`: ヒストグラムの長さ。
  * `histRNA::Array`: RNAヒストグラム。
  * `bins::Vector{Vector}`: 生細胞記録時間ビンの数。
  * `DwellTimes::Vector{Vector}`: 滞留時間。
  * `DTtypes::Vector`: 滞留時間のタイプ。
