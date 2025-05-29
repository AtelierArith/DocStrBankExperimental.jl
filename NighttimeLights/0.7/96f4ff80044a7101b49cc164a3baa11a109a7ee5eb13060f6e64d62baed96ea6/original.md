The time series of a pixel may show a few outliers, but as a whole the pixel may be of importantance in measuring economic activity. The outlier_hampel function uses replaces the outlier observations with interpolated values. This is done using the tsclean function the forecast package of R.

```julia
outlier_hampel(radiance_pixel_ts)
```
