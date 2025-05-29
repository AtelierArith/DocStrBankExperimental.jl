```
savePixelsToFITS(map::HealpixMap{T}, f::CFITSIO.FITSFile, column) where {T <: Number}
```

Save the pixels of `map` into the column with index/name `column` in the FITS file, which must have been already opened.
