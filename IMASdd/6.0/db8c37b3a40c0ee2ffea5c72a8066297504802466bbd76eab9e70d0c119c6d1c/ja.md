```
new_timeslice!(@nospecialize(ids::IDS), time0::Float64=global_time(ids))
```

与えられたidsの下にあるすべての時間依存配列構造の最後の時間スライスの深いコピーを、時間`time0`で再帰的に追加します。
