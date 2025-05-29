```
resample(uv::AbstractUncertainValue, constraint::NoConstraint)
```

Resample an uncertain value without contraints (use the full furnishing distribution).

## Example

```julia
uncertainval = UncertainValue(0, 0.2, Normal)

# Resample the uncertain value by resampling the full distribution once.
resample(uncertainval, NoConstraint())
```
