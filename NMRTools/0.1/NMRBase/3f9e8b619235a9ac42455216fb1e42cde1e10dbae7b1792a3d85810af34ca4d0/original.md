```
label(nmrdata)
label(nmrdata, dim)
label(nmrdimension)
```

Return a short label associated with an `NMRData` structure or an `NMRDimension`. By default, for a spectrum this is obtained from the first line of the title file. For a frequency dimension, this is normally something of the form `1H chemical shift (ppm)`.

See also [`label!`](@ref).
