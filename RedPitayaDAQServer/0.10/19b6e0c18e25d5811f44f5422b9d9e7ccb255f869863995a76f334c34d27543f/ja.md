```
SampleChunk
```

サンプルと関連する `PerformanceData` の行列を含む構造体

# フィールド

  * `samples::Matrix{Int16}`: `n`x`m` 行列で、`n` チャンネルの `m` サンプルを含む
  * `performance::Vector{PerformanceData}`: サンプルを送信した各 RedPitaya の `PerformanceData` オブジェクト
