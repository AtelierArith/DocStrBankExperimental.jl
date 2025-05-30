```
getsensitivity(mag; sigma, nbox=15)

getsensitivity(mag, pixdim; sigma_mm=7, nbox=15)

getsensitivity(mag::NIVolume, datatype=eltype(mag); sigma_mm=7, nbox=15)
```

Calculates the bias field using the `boxsegment` approach. It assumes that there is a "main tissue" that is present in most areas of the object. If not set, sigma*mm defaults to 7mm, with a maximum of 10% FoV. The sigma*mm value should  correspond to the bias field, for a faster changing bias field this needs to be smaller. Published in [CLEAR-SWI](https://doi.org/10.1016/j.neuroimage.2021.118175).

See also [`makehomogeneous`](@ref)
