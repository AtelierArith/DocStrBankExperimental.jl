```
intensities_encode(x)
intensities_encode(x, q1)
intensities_encode(x, q1, q2)
```

Performs a linear and monotonous transformation on the data set `x` to fit it into the interval [0.0, 1.0]. It returns the transformed data set as a first result and the information to reverse the tranformation as a second result. If you are only interested in the transformed values, you can use the function `intensities`.

If `q1` is specified, all values below or equal to the quantile specified  by `q1` are mapped to 0.0. All values above or equal to the quantile specified by `q2` are mapped to 1.0. `q2` defaults to `1 - q1`.

The quantiles are calculated per column/variable.

See also `intensities_decode` for the reverse transformation.
