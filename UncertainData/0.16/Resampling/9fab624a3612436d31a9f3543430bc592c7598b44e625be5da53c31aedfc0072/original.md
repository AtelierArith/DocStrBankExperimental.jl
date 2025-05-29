```
resample(udata::UncertainIndexValueDataset, 
    grid::InterpolationGrid;
    trunc::TruncateQuantiles = TruncateQuantiles(0.001, 0.999))
```

Draw a realization of `udata`, then interpolate the data values to `grid`. 

To avoid very large spans of interpolation, the uncertain indices are truncated to some  large quantile range. Values are not truncated. 
