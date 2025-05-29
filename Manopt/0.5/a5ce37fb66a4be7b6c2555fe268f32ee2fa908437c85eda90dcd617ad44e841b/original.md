```
asymptote_export_SPD(filename)
```

export given `data` as a point on a `Power(SymmetricPOsitiveDefinnite(3))}` manifold of one-, two- or three-dimensional data with points on the manifold of symmetric positive definite matrices.

# Input

  * `filename`        a file to store the Asymptote code in.

# Optional arguments for the data

  * `data`            a point representing the 1D, 2D, or 3D array of SPD matrices
  * `color_scheme`    a `ColorScheme` for Geometric Anisotropy Index
  * `scale_axes=(1/3,1/3,1/3)`: move symmetric positive definite matrices closer to each other by a factor per direction compared to the distance estimated by the maximal eigenvalue of all involved SPD points

# Optional arguments for asymptote

  * `camera_position`  position of the camera scene (default: atop the center of the data in the xy-plane)
  * `target`           position the camera points at (default: center of xy-plane within data).

Both values `camera_position` and `target` are scaled by `scaledAxes*EW`, where `EW` is the maximal eigenvalue in the `data`.
