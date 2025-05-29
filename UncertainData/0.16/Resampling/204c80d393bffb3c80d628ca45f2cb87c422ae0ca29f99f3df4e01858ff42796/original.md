```
resample(uv::AbstractUncertainScalarKDE, constraint::TruncateMaximum)
```

Resample `uv` by first truncating the kernel density estimate of the distribution furnishing the value at some maximum value, then resampling it once.

## Example

```julia
# Uncertain value represented by a normal distribution with mean = 0 and
# standard deviation = 1.
uncertainval = UncertainValue(rand(Normal(0, 1), 1000))

constraint = TruncateMaximum(0.8) # accept no values larger than 1.1

# Resample the uncertain value by truncating the distribution furnishing it,
# then resampling the new distribution 700 times.
resample(uncertainval, constraint, 700)
```
