```
Lags
```

Wrapper type for lags used when performing custom state space reconstructions. Used in combination with `Positions` to specify how a `CustomReconstruction` should be constructed.

## Examples

  * `Lags(2, 0, -3, 1)` indicates a 4-dimensional state space reconstruction where    the first variable has a positive lag of 2,    the second variable is not lagged,    the third variable has a lag of -3,    and the fourth variable has a positive lag of 1.
  * `Lags(0, 0)` indicates a 2-dimensional state space reconstruction where both    variables are not lagged.
