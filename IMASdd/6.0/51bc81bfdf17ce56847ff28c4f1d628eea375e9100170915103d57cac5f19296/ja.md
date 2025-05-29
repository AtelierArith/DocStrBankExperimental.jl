```
trim_time!(@nospecialize(ids::IDS), time_range::Tuple{Float64,Float64}; trim_pulse_schedule::Bool=false)
```

`time_range`の外にあるすべての時間依存データを再帰的に削除します。
