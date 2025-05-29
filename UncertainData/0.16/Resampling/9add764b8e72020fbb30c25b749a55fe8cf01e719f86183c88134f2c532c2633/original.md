```
resample(uv::AbstractUncertainScalarKDE, constraint::TruncateLowerQuantile)
```

Resample `uv` by first truncating below the kernel density estimate of the distribution furnishing the value at some lower quantile, then resampling it once.

## Example

```julia
using UncertainData

some_sample = rand(Normal(), 1000)

# Calling UncertainValue with a single vector of numbers triggers KDE estimation
uncertainval = UncertainValue(some_sample) # -> UncertainScalarKDE

constraint = TruncateLowerQuantile(0.16)

# Resample the uncertain value by truncating the distribution furnishing it,
# then resampling the new distribution once.
resample(uncertainval, constraint)
```
