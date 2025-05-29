```
resample(uv::AbstractUncertainScalarKDE, constraint::NoConstraint)
```

Resample without contraints (use the full distribution representing the value)

## Example

```julia
some_sample = rand(Normal(), 1000)

# Calling UncertainValue with a single vector of numbers triggers KDE estimation
uncertainval = UncertainValue(some_sample) # -> UncertainScalarKDE

# Resample the uncertain value by resampling the full distribution once.
resample(uncertainval, NoConstraint())
```
