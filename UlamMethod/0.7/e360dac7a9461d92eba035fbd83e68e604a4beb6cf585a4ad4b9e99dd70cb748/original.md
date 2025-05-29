```
struct StationaryReinjection
```

Reinject the data weighted by the stationary distribution of `P_open`.

### Fields

  * `fallback`: The `ReinjectionAlgorithm` to apply in case the stationary distribution can not be computed.

### Constructor

```
StationaryReinjection(; fallback = DataReinjection())
```
