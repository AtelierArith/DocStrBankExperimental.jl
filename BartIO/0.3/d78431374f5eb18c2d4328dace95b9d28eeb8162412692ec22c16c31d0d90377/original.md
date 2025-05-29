```
read_cfl(filename::String)
```

  * read_cfl(filename(no extension)) -> Array{ComplexF32,N} where N is defined the filename.hdr file
  * read_cfl(filename.cfl) -> Array{ComplexF32,N} where N is defined the filename.hdr file
  * read_cfl(filename.hdr) -> Array{ComplexF32,N} where N is defined the filename.hdr file

Reads complex data from files created by the Berkeley Advanced Reconstruction Toolbox (BART). The output is an Array of ComplexF32 with the dimensions stored in a .hdr file.

## Parameters:

  * filename:   path and filename of the cfl and hdr files, which can either be without extension, end on .cfl, or end on .hdr
