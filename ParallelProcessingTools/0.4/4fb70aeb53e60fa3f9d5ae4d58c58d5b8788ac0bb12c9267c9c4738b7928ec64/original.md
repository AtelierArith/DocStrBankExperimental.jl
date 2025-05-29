```
sleep_ns(t_in_ns::Real)
```

Sleep for `t_in_ns` nanoseconds, using a mixture of `yield()`, `sleep(0)` and `sleep(t)` to be able sleep for short times as well as long times with good relative precision.

Guaranteed to `yield()` at least once, even if `t_in_ns` is zero.
