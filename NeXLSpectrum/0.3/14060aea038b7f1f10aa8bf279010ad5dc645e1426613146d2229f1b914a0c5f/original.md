```
buildfilter(::Type{GaussianFilter}, det::Detector, a::AbstractFloat=1.0, b::AbstractFloat=6.0)::TopHatFilter
```

Build a top-hat filter with Gaussian shape whose width varies with the detector's resolution as a function of X-ray energy for the specified detector with the specified top and base parameters. The `a` parameter corresponds to the filter width relative to the detector resolution expressed as Gaussian width.  So `a=1` is a filter whose width equals the detector resolution at each energy.  The `b` parameter is the extent of the filter in Gaussian widths.  The default `a=1, b=5` corresponds to a  filter that has the same resolution as the detector and an extent of 2.5 Gaussian widths above and below the center channel.
