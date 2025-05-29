```
resample(uv::AbstractUncertainValue, constraint::TruncateMaximum)
```

Resample by first truncating the distribution representing the value at some minimum value, then performing the resampling.

## Example

```julia
uncertainval = UncertainValue(0, 0.8, Normal)
constraint = TruncateMaximum(1.1) # accept no values larger than 1.1

# Resample the uncertain value by truncating the distribution furnishing it,
# then resampling the new distribution once.
resample(uncertainval, constraint)
```
