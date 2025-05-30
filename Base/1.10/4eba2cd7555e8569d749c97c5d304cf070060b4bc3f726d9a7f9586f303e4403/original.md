```
timedwait(testcb, timeout::Real; pollint::Real=0.1)
```

Waits until `testcb()` returns `true` or `timeout` seconds have passed, whichever is earlier. The test function is polled every `pollint` seconds. The minimum value for `pollint` is 0.001 seconds, that is, 1 millisecond.

Return `:ok` or `:timed_out`.
