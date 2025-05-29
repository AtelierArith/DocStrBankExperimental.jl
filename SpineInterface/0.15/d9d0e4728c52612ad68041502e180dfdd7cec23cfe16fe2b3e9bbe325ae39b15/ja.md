```
t_highest_resolution_sets!(mapping)
```

与えられた `Dict`（`TimeSlice` から `Set` へのマッピングである必要があります）をその場で修正し、もしキー `t1` がキー `t2` を含む場合、前者を削除し、その値を後者にマージします。
