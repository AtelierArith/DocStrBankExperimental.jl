```
currentsfromto(currents, src[, dst])
```

Finds the total current from `src` to `dst` regions. If `dst` is not provided, the current from `src` to all other sites is returned.

## Arguments

  * `currents`: The `AbstractCurrents` object to process.
  * `src`: The source region.
  * `dst`: The destination region.

Both `src` and `dst` can be a site/collection of sites or a `LatticeValue{Bool}` mask.
