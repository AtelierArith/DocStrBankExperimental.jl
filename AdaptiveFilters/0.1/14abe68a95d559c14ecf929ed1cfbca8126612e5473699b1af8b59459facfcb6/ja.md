```
focused_adaptive_filter(y, band, fs, args...; kwargs...)
```

特定の周波数範囲に注意を集中させる適応フィルターです。

#引数:

  * `y`: 入力信号
  * `band`: 周波数帯域のタイプ
  * `fs`: サンプリングレート、例: 44100
  * `args`: `adaptive_filter`に渡される引数
  * `kwargs`: `adaptive_filter`に渡されるキーワード引数
