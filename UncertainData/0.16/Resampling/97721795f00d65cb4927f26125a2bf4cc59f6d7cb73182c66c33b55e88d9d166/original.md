```
resample(uv::AbstractUncertainValue, constraint::TruncateQuantiles, n::Int)
```

Resample by first truncating the distribution representing the value at a set of qunatiles, then performing the resampling.

## Example

```julia
uncertainval = UncertainValue(0, 1, Uniform)
constraint = TruncateLowerQuantile(0.2)

# Resample the uncertain value by truncating the distribution furnishing it,
# then resampling the new distribution 1000 times.
resample(uncertainval, constraint, 1000)
```
