```
idle_sleep(n_idle::Integer, t_interval_s, t_max_s)
```

Sleep because something has been idle for `n_idle` times.

Will sleep for `log2(n_idle + 1) * t_interval_s` seconds, but at most for `t_max_s` seconds.

Guaranteed `yield()` at least once, even if `n_idle` is zero.
