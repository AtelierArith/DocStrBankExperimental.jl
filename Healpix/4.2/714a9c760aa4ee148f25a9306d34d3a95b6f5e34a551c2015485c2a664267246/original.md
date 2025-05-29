```
readAlmFromFITS{T <: Complex}(f::CFITSIO.FITSFile, t::Type{T}) -> Alm{T}
readAlmFromFITS{T <: Complex}(fileName::String, t::Type{T}) -> Alm{T}
```

Read a set of a_ℓm coefficients from a FITS file. If the code fails, CFITSIO will raise an exception. (Refer to the CFITSIO library for more information.)
