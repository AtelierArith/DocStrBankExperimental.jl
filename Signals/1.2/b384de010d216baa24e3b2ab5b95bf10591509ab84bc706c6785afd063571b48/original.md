```
s = buffer(input; buf_size = Inf, timespan = 1, type_stable = false)
```

Create a signal who buffers updates to signal `input` until maximum size of `buf_size` or until `timespan` seconds have passed. The signal value is the last full buffer emitted or an empty vector if the buffer have never been filled before.

Buffer type will be `Any` unless `type_stable` is set to `true`, then it will be set to the value of the first encountered item.
