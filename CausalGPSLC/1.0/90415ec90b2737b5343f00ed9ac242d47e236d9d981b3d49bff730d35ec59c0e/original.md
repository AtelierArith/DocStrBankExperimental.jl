```
saveGPSLCObject(g, filename)
saveGPSLCObject(g, "path/to/filename")
saveGPSLCObject(g, "path/to/filename.gpslc")
```

This function will save the [`GPSLCObject`](@ref) `g` to the file `<filename>.gpslc`. This [`GPSLCObject`](@ref), including the posterior samples contained within it can be retrieved with the [`loadGPSLCObject`](@ref) function.

Note: The extension `.gpslc` is optional and will be added if it is not included.
