```
idle_sleep(n_idle::Integer, t_interval_s, t_max_s)
```

`n_idle` 回アイドル状態になったため、スリープします。

`log2(n_idle + 1) * t_interval_s` 秒間スリープしますが、最大で `t_max_s` 秒間です。

`n_idle` がゼロであっても、少なくとも一度は `yield()` が保証されます。
