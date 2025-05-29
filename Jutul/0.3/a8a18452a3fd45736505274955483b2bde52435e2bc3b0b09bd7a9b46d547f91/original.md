```
u1_val = si_units(u1)
meter = si_units(:meter)
meter, hour = si_units(:meter, :hour)
```

Get multiplicative SI unit conversion factors for multiple units simultaneously. The return value will be a `Tuple` of values, one for each input argument. Each input arguments can be either a `String` a `Symbol`.

# Examples

```jldoctest
julia> meter, hour = si_units(:meter, :hour)
(1.0, 3600.0)
```
