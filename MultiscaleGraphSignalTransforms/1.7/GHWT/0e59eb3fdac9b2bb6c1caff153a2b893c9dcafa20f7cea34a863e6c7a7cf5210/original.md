```
dmatrix = ghwt_analysis!(G::GraphSig, GP::GraphPart = nothing, c2f::Bool = true)
```

For a GraphSig object `G`, generate the matrix of GHWT expansion coefficients

### Input Arguments

  * `G::GraphSig`: an input GraphSig object
  * `GP::GraphPart`: an input GraphPart object (optional); after this function is run, `GP`'s `compinfo`, `tag`, etc. are filled

### Output Argument

  * `dmatrix::Array{Float64,3}`: the 3D array of expansion coefficients (i.e., for each input signal vector, the matrix of coefficients; hence, for multiple input signals, the coefficients are organized as a 3D array)
