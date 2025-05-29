```
writeAlmToFITS(f::CFITSIO.FITSFile, alm::Alm{Complex{T}}) where {T <: Number}
writeAlmToFITS(fileName, alm::Alm{Complex{T}}; overwrite = true) where {T <: Number}
```

Write a set of a_ℓm coefficients into a FITS file. If the code fails, CFITSIO will raise an exception. (Refer to the CFITSIO library for more information.) In the fits file the alms are written with explicit index scheme, $\mathrm{index} = \ell^2 + \ell + m + 1$, possibly out of order (check `almExplicitIndex`).
