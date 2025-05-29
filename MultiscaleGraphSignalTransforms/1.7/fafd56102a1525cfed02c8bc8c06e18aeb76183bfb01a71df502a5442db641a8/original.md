```
dmatrix = dvec2dmatrix(dvec::Matrix{Float64}, GP::GraphPart, BS::BasisSpec)
```

Given a vector of expansion coefficients, convert it to a matrix.

### Input Arguments

  * `dvec::Matrix{Float64}`: a vector of expansion coefficients
  * `GP::GraphPart`: a GraphPart object
  * `BS::BasisSpec`: a BasisSpec object

### Output Argument

  * `dmatrix::Array{Float64,3}`: a set of matrices of expansion coefficients
