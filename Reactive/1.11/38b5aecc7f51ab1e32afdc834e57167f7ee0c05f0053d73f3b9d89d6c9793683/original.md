```
filter(f, signal)
```

remove updates from the `signal` where `f` returns `false`. The filter will hold the current value of the signal until `f(value(signal))` returns true.
