```
resample(uv::AbstractUncertainValue, constraint::TruncateMinimum)
```

Resample by first truncating the distribution representing the value at some minimum value, then performing the resampling.

## Example

```julia
uncertainval = UncertainValue(0, 0.2, Normal)
constraint = TruncateMinimum(-0.5) # accept no values less than -0.5

# Resample the uncertain value by truncating the distribution furnishing it,
# then resampling the new distribution once.
resample(uncertainval, constraint)
```
