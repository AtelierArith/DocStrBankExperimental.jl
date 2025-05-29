```
resample(x::AbstractUncertainValueDataset, resampling::ConstrainedValueResampling)
```

Resample `x` by first constraining the supports of the distributions/populations  furnishing the uncertain values, then drawing samples from the limited supports.

Sampling is done without assuming any sequential dependence between the  elements of `x`, such no that no dependence is introduced in the draws beyond what  is potentially already present in the collection of values.

## Example

```julia
# Some example data 
N = 50
x_uncertain = [UncertainValue(Normal, x, rand(Uniform(0.1, 0.8))) for x in rand(N)]
y_uncertain = [UncertainValue(Normal, y, rand(Uniform(0.1, 0.8))) for y in rand(N)]
x = UncertainValueDataset(x_uncertain)
y = UncertainValueDataset(y_uncertain)

# Resample with different constraints
resample(x, ConstrainedValueResampling(TruncateStd(1.5))
resample(y, ConstrainedValueResampling(TruncateStd(0.5))
resample(y, ConstrainedValueResampling(TruncateQuantiles(0.2, 0.8))
```
