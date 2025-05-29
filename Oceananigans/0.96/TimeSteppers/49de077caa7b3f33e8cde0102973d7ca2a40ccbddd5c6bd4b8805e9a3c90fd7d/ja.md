```
mutable struct Clock{T, FT}
```

現在の `time`、`last_Δt`、`iteration` 数、および時間ステッピング `stage` を追跡します。`stage` はマルチステージ時間ステッピング法のみに対して更新されます。`time::T` は数値または `DateTime` オブジェクトのいずれかです。
