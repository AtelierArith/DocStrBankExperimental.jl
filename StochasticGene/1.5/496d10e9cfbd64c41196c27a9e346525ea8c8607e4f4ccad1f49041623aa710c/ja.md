```
TraceData{labelType,geneType,traceType}
```

トレースデータを格納するための構造体。

# フィールド

  * `label::labelType`: データセットのラベル。
  * `gene::geneType`: 遺伝子名（大文字と小文字を区別）。
  * `interval::Float64`: トレースポイント間の時間間隔。
  * `trace::traceType`: トレースデータ。
