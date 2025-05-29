```
intensities_decode(x, its)
```

Backtransforms the intensity values in the data set `x` (values in the interval [0.0, 1.0])`to the range of the original values and returns the new data set or vector. The`its`argument contains the information about the transformation, as it is returned by`intensities_encode`.

Note that the range is truncated if the original transformation used other quantiles than 0.0 or 1.0 (minimum and maximum).

# Example:

```
x = randn(5, 4)
xint, its = intensities_encode(x, 0.05)
dbm = fitdbm(xint)
xgen = samples(dbm, 5)
intensities_decode(xgen, its)
```
