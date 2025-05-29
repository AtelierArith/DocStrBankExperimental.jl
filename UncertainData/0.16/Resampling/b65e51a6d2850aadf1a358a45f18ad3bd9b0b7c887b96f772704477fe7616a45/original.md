```
resample(uv::AbstractUncertainValue, constraint::TruncateUpperQuantile)
```

Resample by first truncating the distribution representing the value at an upper quantile, then performing the resampling.

## Example

```julia
uncertainval = UncertainValue(0, 0.2, Normal)
constraint = TruncateUpperQuantile(0.8)

# Resample the uncertain value by truncating the distribution furnishing it,
# then resampling the new distribution once.
resample(uncertainval, constraint)
```
