```
write_cfl(filename::String,dataCfl::Array{ComplexF32})
```

  * write_cfl(filename(no extension),Array{ComplexF32})
  * write_cfl(filename.cfl, Array{ComplexF32})
  * write_cfl(filename.hdr,Array{ComplexF32})

Write complex data to files following the convention of the Berkeley Advanced Reconstruction Toolbox (BART). The input is an Array of ComplexF32 with the dimensions stored in a .hdr file.

## Parameters:

  * filename:   path and filename of the cfl and hdr files, which can either be without extension, end on .cfl, or end on .hdr
  * Array{ComplexF32,N}:   Array of ComplexF32 corresponding to image/k-space
