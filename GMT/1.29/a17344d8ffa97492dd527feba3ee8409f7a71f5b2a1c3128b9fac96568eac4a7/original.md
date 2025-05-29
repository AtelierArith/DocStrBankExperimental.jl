```
gdaldrivers(type="raster"; out::Bool=false)
```

List all the GDAL drivers available in this GMT.jl installation. By default it prints the names of the raster drivers, but if `type="vector"` it will print the names of the vector drivers. If `out=true`, instead of printing a table it will return the four columns of the table in separate 4 vectors.
