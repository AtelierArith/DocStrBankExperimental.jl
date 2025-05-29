```
consecutive_overlapping_subspans(span::AlignedSpan, duration::Period,
                                 hop_duration::Period)
consecutive_overlapping_subspans(span::AlignedSpan, n_window_samples::Int, n_hop_samples::Int)
```

`AlignedSpan` のイテレータを作成します。各 `AlignedSpan` は `n_window_samples`（`duration` が `Period` として供給された場合、`n_samples(span.sample_rate, duration)` として計算されます）サンプルを持ち、連続するスパン間で `n_hop_samples`（`hop_duration` が `Period` として供給された場合、`n_samples(span.sample_rate, hop_duration)` として計算されます）サンプルだけシフトされます。

!!! warning
    `n_samples(span)` が `n_window_samples` の整数倍でない場合、`n_window_samples` サンプルを持つ `AlignedSpans` のみが返されます。これは `keep_last=false` の `consecutive_subspans` に類似しており、`consecutive_subspans` のデフォルトの動作ではありません。


注意: `hop_duration` が整数のサンプル数として表現できない場合、すべての出力 `AlignedSpans` が同じサンプル数を持つように丸めが行われます。丸めが行われると、出力 `hop_duration` は次のようになります: `Nanosecond(n_samples(samp_rate, hop_duration) / samp_rate * 1e9)`
