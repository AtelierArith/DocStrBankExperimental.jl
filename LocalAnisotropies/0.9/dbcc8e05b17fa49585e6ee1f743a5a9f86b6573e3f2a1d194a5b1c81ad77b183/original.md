```
adjust_rake(localaniso, azimuths)
adjust_rake!(localaniso, azimuths)
```

Adjust the main direction :X along the azimuth informed. This will change the directions of :X and :Y, and keep the :Z unchanged Useful when the ellipsoid has the correct :Z (e.g. along body thickness), but the main direction should align with an specific azimuth onto the main plane.

## Example

Considering three ellipsoids in the `localaniso` variable

```julia
azimuths = [25.0, 30.0, 40.0]
newpars = adjust_rake(localaniso, azimuths)
```
