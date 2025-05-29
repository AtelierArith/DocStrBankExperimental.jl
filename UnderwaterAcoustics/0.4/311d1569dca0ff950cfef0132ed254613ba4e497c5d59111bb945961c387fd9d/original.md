```
impulse_response(pm, tx, rx, fs; abstime=false, ntaps=nothing)
```

Compute the impulse response at the receiver `rx` due to the source `tx` using propagation model `pm` at the given sampling frequency `fs`. If `abstime` is `true`, the result is in absolute time from the start of transmission. Otherwise, the result is relative to the earliest arrival time of the signal at the receiver (possibly with some guard period to accommodate acausal response). `ntaps` specifies the number of taps in the impulse response. If not specified, the number of taps is chosen automatically based on the arrival times.
