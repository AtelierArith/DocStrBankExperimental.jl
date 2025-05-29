```
saveToFITS{T, O <: Order}(map::HealpixMap{T, O},
                          f::CFITSIO.FITSFile,
                          column)
saveToFITS{T, O <: Order}(map::HealpixMap{T, O},
                          fileName::String,
                          typechar="D",
                          unit="",
                          extname="MAP")
```

Save a Healpix map in the specified (1-based index) column in a FITS file. If the code fails, CFITSIO will raise an exception. (Refer to the CFITSIO library for more information.)
