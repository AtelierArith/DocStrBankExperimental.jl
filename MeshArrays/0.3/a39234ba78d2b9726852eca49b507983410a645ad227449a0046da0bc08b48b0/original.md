```
interpolation_setup(fil::String)
```

Read e.g. `interp_coeffs_halfdeg.jld2`

```
fil=joinpath(tempdir(),"interp_coeffs_halfdeg.jld2")
λ=MeshArrays.interpolation_setup(fil)
```
