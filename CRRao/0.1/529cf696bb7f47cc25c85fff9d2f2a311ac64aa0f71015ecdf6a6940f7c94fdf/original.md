```julia
BPTest(container::FrequentistRegression, data::DataFrame)
```

Perform the Brush-Pegan test. This test only works with linear regression.

# Example

```julia
using CRRao, RDatasets, StatsModels

# Get the dataset
mtcars = dataset("datasets", "mtcars")

# Train the model
container = fit(@formula(MPG ~ HP + WT + Gear), mtcars, LinearRegression())

# Get the BPTest
BPTest(container, mtcars)
```
