```
viz(meta, var; args)
```

Visualize Vlasiator output `var` in `meta` with various options:

## Keyword arguments

  * `axisunit`   - unit of axis of type `AxisUnit`
  * `colorscale` - scale of colormap of type `ColorScale`
  * `normal`     - slice normal direction
  * `vmin`       - minimum color value
  * `vmax`       - maximum color value
  * `comp`       - selection of vector components

### Notes

  * This function will only work in the presence of a Makie.jl backend via package extensions in Julia v1.9 or later versions of the language.
