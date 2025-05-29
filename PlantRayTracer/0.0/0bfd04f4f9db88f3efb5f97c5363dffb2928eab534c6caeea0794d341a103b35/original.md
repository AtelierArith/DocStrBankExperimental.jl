```
tau(vals...)
```

Generate values of transmisivity to be used in material object. `vals...` is a list of one or more comma-separated values, corresponding to the different wavelengths/wavebands to be simulated in a ray tracer.

## Examples

```jldoctest
julia> tau(1.0, 0.0, 2.0);
```
