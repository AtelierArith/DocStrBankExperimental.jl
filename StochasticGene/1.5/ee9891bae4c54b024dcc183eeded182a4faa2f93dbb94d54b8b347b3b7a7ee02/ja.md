```
RNAOnOffData
```

RNA ON/OFF 時間データを格納するための構造体。

# フィールド

  * `label::String`: データセットのラベル。
  * `gene::String`: 遺伝子名（大文字と小文字を区別）。
  * `nRNA::Int`: ヒストグラムの長さ。
  * `histRNA::Vector`: RNA ヒストグラム。
  * `bins::Vector`: 生細胞記録時間ビンの数。
  * `ON::Vector`: ON 時間確率密度。
  * `OFF::Vector`: OFF 時間確率密度。
