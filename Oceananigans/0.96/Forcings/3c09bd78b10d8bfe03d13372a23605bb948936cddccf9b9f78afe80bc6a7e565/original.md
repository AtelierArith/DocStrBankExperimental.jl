```
Forcing(array::FlavorOfFTS)
```

Return a `Forcing` by a `FieldTimeSeries`, which can be added to the tendency of a model field.

Forcing is computed by calling `fts[i, j, k, Time(clock.time)]`, so the `FieldTimeSeries` must have the spatial dimensions of the `grid`.
