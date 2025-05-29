```
load_clean_components(fname::AbstractString, beam=nothing)
```

Load a clean component model from a file. The file can be a FITS file or a .mod file. If the beam argument is not given it will try to extract the beam from the FITS file.
