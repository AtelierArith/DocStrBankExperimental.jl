```
resample(uv::AbstractUncertainValue, constraint::TruncateRange, n::Int)
```

Resample by first truncating the distribution representing the value at some minimum value, then performing the resampling.

## Example

```julia
uncertainval = UncertainValue(0, 0.8, Normal)
constraint = TruncateRange(-0.7, 1.1) # accept values only in range [-0.7, 1.1]

# Resample the uncertain value `1000` times by truncating the distribution furnishing it,
# then resampling the new distribution `1000` times 
resample(uncertainval, constraint, 1000)
```
