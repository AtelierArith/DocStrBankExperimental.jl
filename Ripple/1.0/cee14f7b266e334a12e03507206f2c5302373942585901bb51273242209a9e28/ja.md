```
NxPacket(timestamp::Int,data::Matrix{Real})
```

個々のデータパケット（ファイルごとに複数の可能性あり）。`timestamp`はこのパケットの時間的オフセット（プロセッサの`clock_frequency`を使用）であり、`data`は2Dの「時間」x「チャネル」マトリックスです。
