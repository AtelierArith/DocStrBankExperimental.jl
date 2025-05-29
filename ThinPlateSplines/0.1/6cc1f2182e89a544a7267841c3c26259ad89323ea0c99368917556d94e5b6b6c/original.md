```
tps_deform(x1, x2, y, λ; compute_affine=true)
```

computes a tps deformation based on `x1`, `y` and `λ` and applies it to `x2`. First `tps_solve` is applied and then `tps_deform`.

# Arguments

```
`x1`: control points for the tps generation
`x2`: coordinates of points to be deformed by the tps.
`y`: deformed control points for the tpd generation
`λ`: stiffness coefficient
`compute_affine`: optional argument defining whether the affine transform is computed.
```

returned are the deformed coordinates as a matrix
