```
reference_magnitude(localaniso, axis)
reference_magnitude!(localaniso, axis)
```

Rescale the magnitudes of `localaniso` by setting `axis` as a unit reference. `axis` can be :X, :Y or :Z.

## Example

For example, consider a point with magnitude equal to [1.0, 0.2]. After scaling it with a ExponentialVariogram of range=10m, the range in X would be 10m and in Y would be 2m at this point. If we first call `reference_magnitude!(localaniso, :Y)`, the magnitude will turn to [5.0, 1.0], and after scaling to the same previous variogram, the range in X would be 50m and in Y would be 10m.
