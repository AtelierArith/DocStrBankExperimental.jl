```
T = mztype(scan)
```

Return the type used to present `m/z` values.

Packages should define this for the scan type, i.e.,

```
MzCore.mztype(::Type{SomeScanType{T,...}}) = T
```
