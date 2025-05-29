```
tps_deform(x2::AbstractArray, tps::ThinPlateSpline)
```

calculate deformed locations of an input vector of positions`x2` according to thin-plate spline. Note that in combination with suitable interpolation packages can this be used to warp an image, but this function does not apply a warp by itself. Yet it can be used to transform other mathematical structures rather than points.

# Arguments

```
`x2`: coordinates of points to be deformed.
`tps`: the thin-plate spline structure of type `ThinPlateSpline` defining the deformation.
```
