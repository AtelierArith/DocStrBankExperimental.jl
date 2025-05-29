```
PowerVariogram(; length, scaling, exponent, nugget)
```

A power variogram with base `length` in length units, and `scaling`, `exponent` and `nugget` parameters.

The base `length` parameter serves to scale the lag `h` in the power variogram formula, i.e. `h -> h / length`.
