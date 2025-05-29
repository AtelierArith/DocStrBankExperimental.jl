```
rho(vals...)
```

Generate values of reflectivity to be used in material object. `vals...` is a list of one or more comma-separated values, corresponding to the different wavelengths/wavebands to be simulated in a ray tracer.

## Examples

```jldoctest
julia> rho(1.0, 0.0, 2.0);
```
