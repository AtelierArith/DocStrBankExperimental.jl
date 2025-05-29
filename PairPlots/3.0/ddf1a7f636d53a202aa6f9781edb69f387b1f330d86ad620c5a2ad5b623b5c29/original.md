```
pairplot(gridpos::Makie.GridPosition, inputs...; kwargs...)
```

Create a pair plot at a given grid position of a Makie figure.

Example

```julia
fig = Figure()
pairplot(fig[2,3], table)
fig
```
