```
resample(uv::AbstractUncertainValue, constraint::TruncateUpperQuantile)
```

Resample by first truncating the distribution representing the value at a lower quantile, then performing the resampling.

## Example

```julia
uncertainval = UncertainValue(0, 0.2, Normal)
constraint = TruncateLowerQuantile(0.16)

# Resample the uncertain value by truncating the distribution furnishing it,
# then resampling the new distribution once.
resample(uncertainval, constraint)
```
