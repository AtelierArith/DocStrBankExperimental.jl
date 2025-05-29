```
throttle(dt, input::AbstractObservable)
```

Throttle a signal to update at most once every `dt` seconds. The throttled signal holds the last update of the `input` signal during each `dt` second time window.
