```
sequence_exists(udata::AbstractUncertainValueDataset, c::StrictlyDecreasing{StartToEnd})
```

データセットを通じて厳密に減少するシーケンスは存在しますか？すなわち、各分布を提供された分位範囲に制約をかけた後に厳密に減少するシーケンスが見つかるかどうかを確認します（これは、一部の分布が無限のサポートを持つ可能性があるため、必要です）。
