```
(dvec, BS) = dmatrix2dvec(dmatrix::Array{Float64,3}, GP::GraphPart)
```

Given a matrix of expansion coefficients, convert it to a vector.

### Input Arguments

  * `dmatrix::Array{Float64,3}`: matrices of expansion coefficients
  * `GP::GraphPart`: an input GraphPart object
  * `BS::BasisSpec`: an input BasisSpec object

### Outputs Arguments

  * `dvec::Matrix{Float64}`: a vector of expansion coefficients
  * `BS::BasisSpec`: an output BasisSpec object
