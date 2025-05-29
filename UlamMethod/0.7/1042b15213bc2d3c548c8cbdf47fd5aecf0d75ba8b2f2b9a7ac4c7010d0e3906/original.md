```
viz(object; kwargs...)
```

This function wraps `Meshes.viz` for `UlamMethod` objects for plotting.

### Methods

```
viz(boundary; kwargs...)
```

Plot a boundary.

```
viz(bins; kwargs...)
```

Plot the bins.

```
viz(binner; kwargs...)
```

Plot `binner.bins`.

```
viz(data; kwargs...)
```

Plot a `2 x N` matrix of points.

```
viz(traj; kwargs...)
```

Plot `traj.x0` and `traj.xT` on the same graph.

```
viz(ulam; bins_labels = true, bins_labels_size = 16)
```

Plot the bins, boundary and a heatmap of the stationary distribution of `P_closed(ulam)`.

Optionally, superimpose bin labels with `bin_labels` and adjust their size with `bins_labels_size`.

```
viz(traj, ulam; bins_labels = true, bins_labels_size = 16)
```

Plot a heatmap of the counts in each bin of both `traj.x0` and `traj.xT`.

Optionally, superimpose bin labels with `bin_labels` and adjust their size with `bins_labels_size`.

---

### The docstring for `Meshes.viz` is provided below.

---

```
viz(object; [options])
```

Visualize Meshes.jl `object` with various `options`.

## Available options

  * `color`        - color of geometries
  * `alpha`        - transparency in [0,1]
  * `colormap`     - color scheme/map from ColorSchemes.jl
  * `colorrange`   - minimum and maximum color values
  * `showsegments` - visualize segments
  * `segmentcolor` - color of segments
  * `segmentsize`  - width of segments
  * `showpoints`   - visualize points
  * `pointmarker`  - marker of points
  * `pointcolor`   - color of points
  * `pointsize`    - size of points

The option `color` can be a single scalar or a vector of scalars. For [`Mesh`](@ref) subtypes, the length of the vector of colors determines if the colors should be assigned to vertices or to elements.

## Examples

Different coloring methods (vertex vs. element):

```
# vertex coloring (i.e. linear interpolation)
viz(mesh, color = 1:nvertices(mesh))

# element coloring (i.e. discrete colors)
viz(mesh, color = 1:nelements(mesh))
```

Different strategies to show the boundary of geometries (showsegments vs. boundary):

```
# visualize boundary with showsegments
viz(polygon, showsegments = true)

# visualize boundary with separate call
viz(polygon)
viz!(boundary(polygon))
```

### Notes

  * This function will only work in the presence of a Makie.jl backend via package extensions in Julia v1.9 or later versions of the language.
