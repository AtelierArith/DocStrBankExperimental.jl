```
strict_push!(s::Signal, val, async = Signals.async_mode())
```

Set `s` to `val` and propagate into derived signals, is `async` is `true`(default) then updates to derived signals will occur asynchronically.
