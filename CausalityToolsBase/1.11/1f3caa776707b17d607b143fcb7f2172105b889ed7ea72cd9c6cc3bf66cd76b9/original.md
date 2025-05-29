```
non0hist(points, ϵ::RectangularBinning, dims)
```

Determine which bins are visited by `points` given the rectangular binning scheme `ϵ`, considering only the marginal along dimensions `dims`. Bins are referenced  relative to the axis minimum.

Returns the unordered histogram (vistitation frequency) over the array of bin visits.

This method extends `ChaosTools.non0hist`.
