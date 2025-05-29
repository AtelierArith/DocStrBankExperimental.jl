```
writeClToFITS(f::CFITSIO.FITSFile, Cl::Vector{T}) where {T <: Real}
writeClToFITS(fileName, Cl::Vector{T}; overwrite = true) where {T <: Real}
```

Write a set of C_ℓ coefficients to a FITS file.
