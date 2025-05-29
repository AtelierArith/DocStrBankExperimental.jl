```
currentsfrom(currents, src)
```

Create a `LatticeValue` object with the currents from `src` region to all other sites.

## Arguments

  * `currents`: The `AbstractCurrents` object to process.
  * `src`: The source region. Can be a site/collection of sites or a `LatticeValue{Bool}` mask.
