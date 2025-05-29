```
(dmatrixf2c, IX) = fine2coarse!(GP::GraphPart;
dmatrix::Array{Float64,3} = zeros(0, 0, 0),
coefp::Bool = false, indp::Bool = false)
```

Fill in the fine-to-coarse info (rs2f2c, tagf2c, and compinfof2c) in a GraphPart object.  Also, rearrange a matrix of expansion coefficients.

### Input Arguments

  * `GP::GraphPart`: an input GraphPart object without fine-to-coarse info (rsf2c, tagf2c, compinfof2c); after this function, rsf2c, tagf2c, compinfof2c are filled. Note that rs, tag, compinfo are intact.
  * `dmatrix::Array{Float64,3}`: a matrix of expansion coefficients in coarse-to-fine arrangement (default: null matrix)
  * `coefp::Bool`: a flag to return the rearranged f2c coefficients (default: false)
  * `indp::Bool`: a flag to return the reordering index (default: false)

### Output Arguments

  * `dmatrixf2c::Array{Float64,3}`: a matrix of expansion coefficients in fine-to-coarse arrangement (if requested)
  * `IX::Vector{Unsigned}`: the reordering index for all levels
