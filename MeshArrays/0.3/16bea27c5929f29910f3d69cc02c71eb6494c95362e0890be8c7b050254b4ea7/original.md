```
UVtoUEVN(u,v,G::NamedTuple)
```

1. Interpolate to grid cell centers (uC,vC)
2. Convert to `Eastward/Northward` components (uE,vN)

Note: land masking `u,v` with `NaN`s preemptively can be adequate.
