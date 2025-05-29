```
go!(s, until)
```

Runs simulation defined by `s` until `s.now` is greater or equal than `until` or `s.event_queue` is empty (i.e. nothing is left to be done). By default `until` equals `Inf`.
