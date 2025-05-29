```
value(d::DataMD; x::Number=[value])
```

Interpolate value of a DataF1 dataset for a given x:

# NOTE:

  * Uses linear interpolation between points.
  * Assumes value is zero when out of x-range.
