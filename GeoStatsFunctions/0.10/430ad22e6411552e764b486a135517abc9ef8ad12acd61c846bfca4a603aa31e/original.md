```
surfplot(f; [options])
```

Plot the geostatistical surface `f` with given `options`.

## Common options

  * `colormap` - Color map
  * `maxlag`   - maximum lag
  * `labels`   - variable names

## Theoretical function options

  * `normal` - Normal direction to plane (default to vertical)
  * `nlags`  - Number of lags (default to `20`)
  * `nangs`  - Number of angles (default to `50`)

## Examples

```julia
# initialize figure with Gaussian variogram
fig = surfplot(GaussianVariogram())

# add spherical variogram to figure
surfplot!(fig, SphericalVariogram())
```

### Notes

This function will only work in the presence of a Makie.jl backend via package extensions in Julia v1.9 or later versions of the language.
