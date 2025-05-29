```
resample(uv::AbstractUncertainScalarKDE, constraint::TruncateQuantiles,
    n::Int)
```

Resample `uv` by first truncating the kernel density estimate of the distribution furnishing the value both above and below at some quantile range, then resampling it `n` times.

## Example

```julia
using UncertainData

some_sample = rand(Normal(), 1000)

# Calling UncertainValue with a single vector of numbers triggers KDE estimation
uncertainval = UncertainValue(some_sample) # -> UncertainScalarKDE

constraint = TruncateQuantiles(0.1, 0.9)

# Resample the uncertain value by truncating the distribution furnishing it,
# then resampling the new distribution 500 times.
resample(uncertainval, constraint, 500)
```
