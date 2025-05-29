```julia
coef(container::FrequentistRegression)
```

Estimated coefficients of the model. Extends the `coef` method from [StatsAPI.jl](https://github.com/JuliaStats/StatsAPI.jl).

# Example

```julia
using CRRao, RDatasets, StatsModels

# Get the dataset
mtcars = dataset("datasets", "mtcars")

# Train the model
container = fit(@formula(MPG ~ HP + WT + Gear), mtcars, LinearRegression())

# Get table of coefficients
coef(container)
```
