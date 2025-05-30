```
interpolation_setup(fil::String)
```

例えば、`interp_coeffs_halfdeg.jld2`を読み込みます。

```
fil=joinpath(tempdir(),"interp_coeffs_halfdeg.jld2")
λ=MeshArrays.interpolation_setup(fil)
```
