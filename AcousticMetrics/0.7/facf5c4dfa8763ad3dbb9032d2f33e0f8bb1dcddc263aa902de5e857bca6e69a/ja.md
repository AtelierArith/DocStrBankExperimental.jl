```
ApproximateOctaveBands{LCU,TF}(bstart::Int, bend::Int)
```

`eltype` `TF` を持つ `ApproximateOctaveBands` を `bstart` から `bend` までのバンドインデックス番号を含むように構築します。

「標準」のバンド周波数は `scaler` によってスケーリングされます。例えば、`scaler = 0.5` の場合、通常の `1000 Hz` の周波数は `500 Hz` になります。
