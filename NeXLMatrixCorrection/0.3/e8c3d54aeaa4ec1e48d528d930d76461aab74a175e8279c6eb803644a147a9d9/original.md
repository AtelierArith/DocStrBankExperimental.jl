```
asa(ElementalMap, krs::AbstractVector{KRatios}, scale=Log3Band)
```

Converts `Vector{KRatios}` into a Dict that maps each Element present to an image.

```
scale = [ Log3Band , Log3BandColorblind, Log3BandBright, LogScale, Gray ]
```
