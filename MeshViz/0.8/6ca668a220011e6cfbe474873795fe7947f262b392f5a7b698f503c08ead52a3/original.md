```
viz(object)
```

Visualize Meshes.jl `object` with various options:

  * `color`       - color of geometries or points
  * `alpha`       - transparency channel in [0,1]
  * `colorscheme` - color scheme from ColorSchemes.jl
  * `facetcolor`  - color of the facets (e.g. edges)
  * `showfacets`  - tells whether or not to show the facets
  * `pointsize`   - size of points in point set
  * `segmentsize` - size (or width) of segments

The option `color` can be a single scalar or a vector of scalars. For meshes, the length of the vector of colors determines if the colors should be assigned to vertices or elements.

## Examples

```
# vertex coloring (i.e. linear interpolation)
viz(mesh, color = 1:nvertices(mesh))

# element coloring (i.e. discrete colors)
viz(mesh, color = 1:nelements(mesh))
```
