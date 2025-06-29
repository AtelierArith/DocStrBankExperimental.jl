```
resample(x::AbstractUncertainIndexValueDataset, resampling::SequentialResampling)
```

Resample `x` according to a sequential resampling constraint. 

This way of resampling introduces some serial dependence between the elements of `x` -  *beyond* what might already be present in the dataset. This is because imposing a  sequential constraint (e.g. `StrictlyIncreasing`) to the `i`-th value of the dataset  imposes constraints on what is possible to sample from the `i+1`th value.

## Example

```julia
# Some example data 
N = 50
x_uncertain = [UncertainValue(Normal, x, rand(Uniform(0.1, 0.8))) for x in rand(N)]
y_uncertain = [UncertainValue(Normal, y, rand(Uniform(0.1, 0.8))) for y in rand(N)]
x = UncertainValueDataset(x_uncertain)
y = UncertainValueDataset(y_uncertain)

time_uncertain = [UncertainValue(Normal, i, 1) for i = 1:length(x)];
time_certain = [CertainValue(i) for i = 1:length(x)];
timeinds_x = UncertainIndexDataset(time_uncertain)
timeinds_y = UncertainIndexDataset(time_certain)

X = UncertainIndexValueDataset(timeinds_x, x)
Y = UncertainIndexValueDataset(timeinds_y, y);

# Resample 
seq_resampling = SequentialResampling(StrictlyIncreasing())
resample(X, seq_resampling)
```
