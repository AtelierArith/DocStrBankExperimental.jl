```
resample(uv::AbstractUncertainValue, constraint::NoConstraint, n::Int)
```

Resample an uncertain value without contraints (use the full furnishing distribution).

## Example

```julia
uncertainval = UncertainValue(0, 0.2, Normal)

# Resample the uncertain value by resampling the full distribution 1000 times.
resample(uncertainval, NoConstraint(), 1000)
```
