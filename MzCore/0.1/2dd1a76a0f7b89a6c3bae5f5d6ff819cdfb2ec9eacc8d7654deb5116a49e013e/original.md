```
T = intensitytype(scan)
```

Return the type used to represent intentities (ion counts).

Packages should define this for the scan type, i.e.,

```
MzCore.intensitytype(::Type{SomeScanType{T,...}}) = T
```
