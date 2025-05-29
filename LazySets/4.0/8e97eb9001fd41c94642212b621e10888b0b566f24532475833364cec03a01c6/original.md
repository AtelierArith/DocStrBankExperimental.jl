```
radius_hyperrectangle(sih::SymmetricIntervalHull, i::Int)
```

Return the box radius of the symmetric interval hull of a set in a given dimension.

### Input

  * `sih` – symmetric interval hull of a set
  * `i`   – dimension of interest

### Output

The radius in the given dimension.

### Notes

If the radius was computed before, this is just a look-up. Otherwise it is computed.
