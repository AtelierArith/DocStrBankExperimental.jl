```
CPDI()
```

A kernel for convected particle domain interpolation (CPDI) [^CPDI]. `CPDI` requires the initial particle length `l` and the deformation gradient `F` in the particle property. For example, in two dimensions, the property is likely to be as follows:

```jl
ParticleProp = @NamedTuple begin
    < variables... >
    l :: Float64
    F :: Mat{2, 2, Float64, 4}
end
```

[^CPDI]: [Sadeghirad, A., Brannon, R.M. and Burghardt, J., 2011. A convected particle domain interpolation technique to extend applicability of the material point method for problems involving massive deformations. International Journal for numerical methods in Engineering, 86(12), pp.1435-1456.](https://doi.org/10.1002/nme.3110)
