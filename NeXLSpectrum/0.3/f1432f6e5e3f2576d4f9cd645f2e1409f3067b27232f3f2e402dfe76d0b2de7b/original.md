```
loadmultispec(path::AbstractString, basefn::AbstractString; indexes=0:3, fnmapper::String = "{1}[{2}].msa")
```

Load multiple spectra using the `basefn` and `fnmapper` to determine which spectra to load.  The spectra should be related in the sense that they were all collected simulataneously so they have the same `:RealTime`, `:BeamEnergy`  and `:LiveTime`.
