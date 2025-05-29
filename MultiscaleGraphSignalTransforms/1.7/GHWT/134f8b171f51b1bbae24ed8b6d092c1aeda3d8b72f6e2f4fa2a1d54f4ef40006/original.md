```
ghwt_core!(GP::GraphPart, dmatrix::Array{Float64,3})
```

performs the forward GHWT transform, which generates expansion coefficients, tag, and compinfo.

### Input Arguments

  * `GP::GraphPart`: a GraphPart object (with or without tag and compinfo data); note that tag and compinfo will be modified after this function is executed
  * `dmatrix::Array{Float64,3}`: a matrix of expansion coefficients with only the last column filled in as the original input signal(s) `f`; after this function is executed, this matrix contains whole expansion coefficients of the input signal(s) relative to the GHWT dictionary
