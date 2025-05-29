```
fpswhen(switch, rate)
```

returns a signal which when `switch` signal is true, updates `rate` times every second. If `rate` is not possible to attain because of slowness in computing dependent signal values, the signal will self adjust to provide the best possible rate.
