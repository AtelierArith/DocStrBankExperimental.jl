```
resample(uv::AbstractUncertainValue, constraint::TruncateStd; n_draws::Int = 10000)
```

Resample by first truncating the distribution representing the value to some multiple  of its standard deviation around the mean.

## Example

```julia
uncertainval = UncertainValue(0, 0.8, Normal)
constraint = TruncateStd(1.1) # accept values only in range 1.1*stdev around the mean

# Resample the uncertain value by truncating the distribution furnishing it,
# then resampling the new distribution 1000 times.
resample(uncertainval, constraint, 1000)
```
