```
filter(f, default, signal)
```

remove updates from the `signal` where `f` returns `false`. The filter will hold the value default until f(value(signal)) returns true, when it will be updated to value(signal).
