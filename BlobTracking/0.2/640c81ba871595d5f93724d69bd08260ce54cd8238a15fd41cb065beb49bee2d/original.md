```
Blob
```

Represents a blob. Internally stores a Kalman filter, a counter that is incremented when the blob is not assigned a measurement and a trace of all locations and all seen measurements. If no measurement was seen for a particular time step, `OOB = CartesianIndex(0,0)` is recorded.

This type supports `location, trace, tracem, lifetime, draw!`
