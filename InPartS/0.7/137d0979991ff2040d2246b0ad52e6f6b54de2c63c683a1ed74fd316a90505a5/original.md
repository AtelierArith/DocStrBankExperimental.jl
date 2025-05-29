```
SaveCallback{backend}(trigger::AbstractCallback, filename, dumprng, warn, onconflict)
```

Create a callback that periodically saves simulation snapshots to `filename`.

# Extended help

A snapshot is saved every time the `trigger` callback is triggered. On first activation, static simulation parameters are saved.

If the two-argument function `dumprng`, called on the `SaveCallback` and Simulation, returns `true`, the full RNG state is dumped to the snapshot.
