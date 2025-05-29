```julia
residuals(container::FrequentistRegression)
```

Residuals of the model. Extends the `residuals` method from [StatsAPI.jl](https://github.com/JuliaStats/StatsAPI.jl).

# Example

```julia
using CRRao, RDatasets, StatsModels

# Get the dataset
mtcars = dataset("datasets", "mtcars")

# Train the model
container = fit(@formula(MPG ~ HP + WT + Gear), mtcars, LinearRegression())

# Get residuals
residuals(container)
```
