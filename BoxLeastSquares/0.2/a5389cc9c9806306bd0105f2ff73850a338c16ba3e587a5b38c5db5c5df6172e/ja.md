```
autoperiod(t, duration;
    minimum_n_transit=3, frequency_factor=1.0,
    [minimum_period, maximum_period])
```

与えられた時間と期間から自動的に周期グリッドを決定します。周期は、少なくとも `minimum_n_trasnit` 回のトランジットが発生するように選択されます。デフォルトの最小周期は最大期間の2倍です。デフォルトの最大周期は `(maximum(t) - minimum(t)) / (minimum_n_transit - 1)` です。周波数ファクターは周波数空間の粒度を変更します - より小さな周波数ファクターは、より細かい周期グリッドを作成します。
