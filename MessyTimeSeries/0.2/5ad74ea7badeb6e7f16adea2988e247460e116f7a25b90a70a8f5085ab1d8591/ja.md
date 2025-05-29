```
kfilter_full_sample!(settings::KalmanSettings, status::SizedKalmanStatus)
```

`t=1` から `history_length` までのカルマンフィルタを実行し、`status` をインプレースで更新します。
