```julia
coeftable(container::FrequentistRegression)
```

Table of coefficients and other statistics of the model. Extends the `coeftable` method from [StatsAPI.jl](https://github.com/JuliaStats/StatsAPI.jl).

# Example

```julia
using CRRao, RDatasets, StatsModels

# Get the dataset
mtcars = dataset("datasets", "mtcars")

# Train the model
container = fit(@formula(MPG ~ HP + WT + Gear), mtcars, LinearRegression())

# Get table of coefficients
coeftable(container)
```
