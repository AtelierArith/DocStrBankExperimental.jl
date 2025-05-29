```
funplot!(fig, f; [options])
```

Mutating version of [`funplot`[@ref] where the figure `fig` is updated with the plot of the geostatistical function `f`.

## Examples

```julia
# initialize figure with Gaussian variogram
fig = funplot(GaussianVariogram())

# add spherical variogram to figure
funplot!(fig, SphericalVariogram())
```

See the documentation of [`funplot`](@ref) for `options`.
