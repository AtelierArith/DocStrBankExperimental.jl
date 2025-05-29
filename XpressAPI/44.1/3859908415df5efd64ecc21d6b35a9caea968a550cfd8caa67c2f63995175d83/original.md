```
XPRSaddcbmipthread(prob, cb, priority)
```

# Arguments

  * `cbprob`: The problem passed to the callback function.
  * `threadprob`: The problem pointer for the MIP thread

`cb` will be invoked with this signature:

```
cb(cbprob, threadprob)::Nothing
```
