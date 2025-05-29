```
resample(udata::UncertainIndexValueDataset, 
    sequential_constraint::SequentialSamplingConstraint,
    grid::InterpolationGrid;
    trunc::TruncateQuantiles = TruncateQuantiles(0.001, 0.999))
```

Draw a realization of `udata`, enforcing a `sequential_constraint` on the indices. Then, interpolate the values of the realization to the provided grid of indices (`grid`). 

To avoid very large spans of interpolation, the uncertain indices are truncated to some  large quantile range. Values are not truncated.  
