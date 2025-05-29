```
rampoff(x,[len=10ms],[fn=x -> sinpi(0.5x)])
```

Ramp the offset of a signal, smoothly transitioning from frull amplitude to 0 amplitude over the course of `len` seconds.

The function should be non-decreasing and should have a domain and range of [0,1]

Both `len` and `fn` are optional arguments: either one or both can be specified, though `len` must occur before `fn` if present.
