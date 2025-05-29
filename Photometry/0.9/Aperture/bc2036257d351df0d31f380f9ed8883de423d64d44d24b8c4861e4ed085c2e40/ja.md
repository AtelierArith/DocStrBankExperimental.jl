```
photometry(::AbstractAperture, data::AbstractMatrix, [error])
photometry(::AbstractVector{<:AbstractAperture}, data::AbstractMatrix, [error])
```

与えられたアパーチャに対して `data` にアパーチャフォトメトリーを実行します。`error`（ピクセルごとの標準偏差）が提供されている場合、合計誤差を計算します。アパーチャのリストが提供されている場合、出力は `TypedTables.Table` になります。それ以外の場合は `NamedTuple` になります。

!!! tip
    このコードは自動的にマルチスレッド化されています。これを活用するために、ランタイムを開始する前に `JULIA_NUM_THREADS` が設定されていることを確認してください。

