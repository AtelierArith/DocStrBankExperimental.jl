```
localvariography(sdata, lpars, var₁, var₂=var₁;
axis=:X, tol=1e-6, maxratio1=Inf, maxratio2=Inf, [optional parameters])
```

Computes an unconventional directional (cross-)variogram for the variables `var₁` and `var₂` of spatial data `sdata`. This uses local anisotropies `lpars` to create pseudo-partitions along local `axis` direction (`axis` ∈ [:X, :Y, :Z]) and the EmpiricalVariogram is calculated with these data. The directional tolerance bandwidth `tol` can be passed. The `maxratio1` and `maxratio2` partially ignore data if magnitude ratios are above these values (does not ignore anything by default). Other optional parameters are defined at `GeoStats.EmpiricalVariogram`, such as `nlags`, `maxlag`, `distance` and `algo`. If axis informed is a combination of two axes (e.g. :XY), this will consider a planar variogram along that plane.

Similar (but not equal) to https://github.com/rmcaixeta/Local_variography
