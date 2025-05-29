```
saveToFITS(map::HealpixMap{T, O}, filename::AbstractString, typechar="D", unit="", extname="MAP") where {T <: Number, O <: Order}
saveToFITS(map::PolarizedHealpixMap{T, O}, filename::AbstractString, typechar="D", unit="", extname="MAP") where {T <: Number, O <: Order}
```

Save a map into a FITS file. The name of the file is specified in `filename`; if it begins with `!`, existing files will be overwritten without warning. The parameter `typechar` specifies the data type to be used in the FITS file: the default (`D`) will save 64-bit floating-point values. See the CCFITSIO documentation for other values. The keyword `unit` specifies the measure unit used for the pixels in the map. The keyword `extname` specifies the name of the HDU where the map pixels will be written.
