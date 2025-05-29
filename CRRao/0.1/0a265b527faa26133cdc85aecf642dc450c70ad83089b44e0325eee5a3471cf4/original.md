```julia
cooksdistance(container::FrequentistRegression)
```

Compute Cook's distance for each observation in a linear model. Extends the `cooksdistance` method from [StatsAPI.jl](https://github.com/JuliaStats/StatsAPI.jl).

# Example

```julia
using CRRao, RDatasets, StatsModels

# Get the dataset
mtcars = dataset("datasets", "mtcars")

# Train the model
container = fit(@formula(MPG ~ HP + WT + Gear), mtcars, LinearRegression())

# Get vector of Cook's distances
cooksdistance(container)
```
