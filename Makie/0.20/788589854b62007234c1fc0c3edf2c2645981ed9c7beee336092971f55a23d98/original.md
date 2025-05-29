```
FileIO.save(filename, scene; size = size(scene), pt_per_unit = 0.75, px_per_unit = 1.0)
```

Save a `Scene` with the specified filename and format.

# Supported Formats

  * `GLMakie`: `.png`
  * `CairoMakie`: `.svg`, `.pdf` and `.png`
  * `WGLMakie`: `.png`

# Supported Keyword Arguments

## All Backends

  * `size`: `(width::Int, height::Int)` of the scene in dimensionless units.
  * `update`: Whether the figure should be updated before saving. This resets the limits of all Axes in the figure. Defaults to `true`.
  * `backend`: Specify the `Makie` backend that should be used for saving. Defaults to the current backend.
  * Further keywords will be forwarded to the screen.

## CairoMakie

  * `pt_per_unit`: The size of one scene unit in `pt` when exporting to a vector format.
  * `px_per_unit`: The size of one scene unit in `px` when exporting to a bitmap format. This provides a mechanism to export the same scene with higher or lower resolution.
