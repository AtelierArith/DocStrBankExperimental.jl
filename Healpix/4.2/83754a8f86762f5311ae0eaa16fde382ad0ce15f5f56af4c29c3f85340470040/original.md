```
readMapFromFITS{T}(f::CFITSIO.FITSFILE, column, t::Type{T})
readMapFromFITS{T}(fileName::String, column, t::Type{T})
```

Read a Healpix map from the specified (1-base indexed) column in a FITS file. The values will be read as numbers of type T. If the code fails, CFITSIO will raise an exception. (Refer to the CFITSIO library for more information.)
