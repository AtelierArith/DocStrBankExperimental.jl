```
resample(uv::AbstractUncertainScalarKDE, constraint::TruncateRange, n::Int)
```

Resample `uv` by first truncating the kernel density estimate of the distribution furnishing the value at some minimum and maximum values, then resampling it `n` times.

## Example

```julia
# Uncertain value represented by a normal distribution with mean = 0 and
# standard deviation = 1.
uncertainval = UncertainValue(rand(Normal(0, 1), 1000))

# Only accept values in the range [-0.9, 1.2]
constraint = TruncateRange(-0.9, 1.2)

# Resample the uncertain value by truncating the distribution furnishing it,
# then resampling the new distribution 300 times.
resample(uncertainval, constraint, 300)
```
