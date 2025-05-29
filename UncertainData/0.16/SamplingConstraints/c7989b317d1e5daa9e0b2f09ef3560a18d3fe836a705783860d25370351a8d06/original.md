```
sequence_exists(x, c::SequentialSamplingConstraint)
```

Does a point-by-point sequence through the uncertain dataset `x` exist that satisfies the criteria `c`?

If `x` is an `UncertainIndexValueDataset`, then check for a sequence through the indices only.

Before the check is performed, the distributions in `x` are truncated to the quantiles provided  by `c` to ensure they have finite supports.

## Example

```julia
# Create a set of time indices 
# We construct this is such a way that we *know* an increasing sequence exists. 
t = [UncertainValue(Normal, i, 2) for i in 1:N];
sequence_exists(t, StrictlyIncreasing(StartToEnd()))
```
