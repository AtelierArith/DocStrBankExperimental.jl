```
kfilter_full_sample(settings::KalmanSettings, status::KalmanStatus=DynamicKalmanStatus())
```

$ t=1, \ldots, T $ の間でカルマンフィルタを実行し、`status` を返します。
