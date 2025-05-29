```
rescale_magnitude(localaniso; r1, r2, r3, clip=[0.05,0.95])
rescale_magnitude!(localaniso; r1, r2, r3, clip=[0.05,0.95])
```

Rescale magnitude values of `localaniso` to desired limits using min-max scaling. `r1`, `r2` and `r3` refer to the ranges along each main axis. `clip` defines the quantiles to which min and max limits are defined. The default is set to [0.05,0.95] to avoid outliers influence.

## Example

In the example below, a 3-D local anisotropy object is rescaled. `r1` has all the values set to 1.0. `r2` and `r3` are rescaled between (0.2, 1.0) and (0.1, 0.5) respectively. That means that if we associate it to a SphericalVariogram of range=10, range1 will be equal to 10 at every place. range2 will vary between 2 and 10. And range3 will vary between 1 and 5.

```julia
example = rescale_magnitude(localaniso3d, r1=1, r2=(0.2,1.0), r3=(0.1,0.5))
```
