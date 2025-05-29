```
asymptote_export_S2_data(filename)
```

Export given `data` as an array of points on the 2-sphere, which might be one-, two- or three-dimensional data with points on the [Sphere](https://juliamanifolds.github.io/Manifolds.jl/stable/manifolds/sphere.html) $\mathbb S^2$.

# Input

  * `filename`                a file to store the Asymptote code in.

# Optional arguments for the data

  * `data`                    a point representing the 1D,2D, or 3D array of points
  * `elevation_color_scheme`  A `ColorScheme` for elevation
  * `scale_axes=(1/3,1/3,1/3)`: move spheres closer to each other by a factor per direction

# Optional arguments for asymptote

  * `arrow_head_size=1.8`: size of the arrowheads of the vectors (in mm)
  * `camera_position`  position of the camera scene (default: atop the center of the data in the xy-plane)
  * `target`           position the camera points at (default: center of xy-plane within data).
