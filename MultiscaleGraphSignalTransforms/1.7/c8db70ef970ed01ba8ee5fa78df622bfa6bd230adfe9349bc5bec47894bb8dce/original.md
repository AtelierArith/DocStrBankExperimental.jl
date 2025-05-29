```
dvec = dmatrix2dvec(dmatrix::Array{Float64,3}, GP::GraphPart, BS::BasisSpec)
```

Given a matrix of expansion coefficients, convert it to a vector. This function assumes that the input coefficient array `dmatrix` is in the coarse-to-fine format. If `BS.c2f == false`, then this function internally converts `dmatrix` into the fine-to-coarse format. Hence, if one supplies the f2c `dmatrix`, the results become wrong, and the subsequent procedure may result in error.

### Input Arguments

  * `dmatrix::Array{Float64,3}`: matrices of expansion coefficients
  * `GP::GraphPart`: an input GraphPart object
  * `BS::BasisSpec`: an input BasisSpec object

### Outputs Arguments

  * `dvec::Matrix{Float64}`: a vector of expansion coefficients
