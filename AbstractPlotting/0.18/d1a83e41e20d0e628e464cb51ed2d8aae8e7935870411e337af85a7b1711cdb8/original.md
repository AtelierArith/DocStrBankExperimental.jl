```
FileIO.save(filename, scene; resolution = size(scene), pt_per_unit = 0.75, px_per_unit = 1.0)
```

Save a `Scene` with the specified filename and format.

# Supported Formats

  * `GLMakie`: `.png`, `.jpeg`, and `.bmp`
  * `CairoMakie`: `.svg`, `.pdf`, `.png`, and `.jpeg`
  * `WGLMakie`: `.png`

# Supported Keyword Arguments

## All Backends

  * `resolution`: `(width::Int, height::Int)` of the scene in dimensionless units (equivalent to `px` for GLMakie and WGLMakie).

## CairoMakie

  * `pt_per_unit`: The size of one scene unit in `pt` when exporting to a vector format.
  * `px_per_unit`: The size of one scene unit in `px` when exporting to a bitmap format. This provides a mechanism to export the same scene with higher or lower resolution.
