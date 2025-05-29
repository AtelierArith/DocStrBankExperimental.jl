```
resample(uv::AbstractUncertainScalarKDE, constraint::TruncateUpperQuantile)
```

Resample `uv` by first truncating above the kernel density estimate of the distribution furnishing the value at some upper quantile, then resampling it once.

## Example

```julia
using UncertainData

some_sample = rand(Normal(), 1000)

# Calling UncertainValue with a single vector of numbers triggers KDE estimation
uncertainval = UncertainValue(some_sample) # -> UncertainScalarKDE

constraint = TruncateUpperQuantile(0.78)

# Resample the uncertain value by truncating the distribution furnishing it,
# then resampling the new distribution once.
resample(uncertainval, constraint)
```
