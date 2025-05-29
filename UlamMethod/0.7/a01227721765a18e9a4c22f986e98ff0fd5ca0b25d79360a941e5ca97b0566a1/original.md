```
struct SourceReinjection{Dim}
```

Reinject the data at particular locations. 

### Fields

  * `points`: A vector of the form `[p1, p2, ...]` where `pi` is a point such as `(x)` or `(x, y)`. Data are reinjected uniformly across all bins that contain at least one member of `points`.
  * `fallback`: The `ReinjectionAlgorithm` to apply in case no bins contain any points or there is no data to reinject.

### Constructor

```
SourceReinjection(points; fallback = DataReinjection())
```
