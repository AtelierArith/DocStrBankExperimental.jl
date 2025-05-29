```
ExactProportionalBands{NO,LCU}(TF=Float64, bstart::Int, bend::Int, scaler=1)
```

`bstart`から`bend`までのバンドインデックス番号を含む`eltype` `TF`の`ExactProportionalBands`を構築します。

「標準」のバンド周波数は`scaler`によってスケーリングされます。例えば、`scaler = 0.5`の場合、通常は`1000 Hz`の周波数が`500 Hz`になります。
