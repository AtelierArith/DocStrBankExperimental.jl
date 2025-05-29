```
readClFromFITS{T <: Real}(f::CFITSIO.FITSFile, t::Type{T}; col_num = 2) -> Vector{T}
readClFromFITS{T <: Real}(fileName::String, t::Type{T}; col_num = 2) -> Vector{T}
```

Read a set of C_ℓ coefficients from a FITS file.
