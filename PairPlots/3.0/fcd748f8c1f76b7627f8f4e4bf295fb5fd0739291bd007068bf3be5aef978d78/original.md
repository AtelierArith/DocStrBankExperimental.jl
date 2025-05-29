```
pairplot(inputs...; figure=(;), kwargs...)
```

Convenience method to generate a new Makie figure with resolution (800,800) and then call `pairplot` as usual. Returns the figure.

Example:

```julia
fig = pairplot(table)
```
