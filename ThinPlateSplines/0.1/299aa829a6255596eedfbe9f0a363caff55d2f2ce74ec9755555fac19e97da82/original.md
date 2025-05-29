```
tps_solve(x,y,λ,compute_affine=true)
```

find solution of tps transformation  (required for some operations but takes additional time.)

# Arguments

```
`x`: control points
`y`: deformed (warped) control points
`λ`: stiffness coefficient
`compute_affine`: computes affine component if `true`
```

returns a `ThinPlateSpline` structure which can be supplied as an argument to `tps_deform`.

# See almost

```
`ThinPlateSpline`
```
