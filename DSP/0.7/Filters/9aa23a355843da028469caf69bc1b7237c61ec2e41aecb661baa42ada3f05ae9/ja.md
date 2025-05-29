```
FIRWindow(; transitionwidth, attenuation=60, scale=true)
```

カイザーウィンドウFIRフィルタ設計。必要なタップ数は、`transitionwidth`（半サイクル/サンプル単位）とストップバンド`attenuation`（dB単位）に基づいて計算されます。`attenuation`のデフォルトは60 dBです。
