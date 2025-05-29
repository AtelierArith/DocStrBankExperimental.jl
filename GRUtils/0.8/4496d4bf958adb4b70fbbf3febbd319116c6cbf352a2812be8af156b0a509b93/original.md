```
viewpoint(rotation, tilt)
```

Set the viewpoint of three-dimensional plots.

`rotation` and `tilt` must be integer values that indicate the "azimuth" and "elevation" angles of the line of sight (in degrees).

If both angles are zero, the plot is viewed in the direction of the Y axis (i.e. the X-Z plane is seen). Positive `rotation` values mean a counterclockwise rotation of the line of sight (or a clockwise rotation of the scene) around the vertical (Z) axis. Positive `tilt` values mean an ascension of the view point.

# Examples

```julia
# Reset the view to the X-Y plane
# (rotation=0, tilt=90)
viewpoint(0, 90)
```
