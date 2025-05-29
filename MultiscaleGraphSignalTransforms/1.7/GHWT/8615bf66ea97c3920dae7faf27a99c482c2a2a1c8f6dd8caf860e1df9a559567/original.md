```
(dvec, BS) = ghwt_bestbasis(dmatrix::Array{Float64,3}, GP::GraphPart; cfspec::Any, flatten::Any = 1.0)
```

Select the overall best basis among the c2f and f2c best bases

### Input Arguments

  * `dmatrix::Array{Float64,3}`: the matrix of expansion coefficients
  * `GP::GraphPart`: an input GraphPart object
  * `cfspec::Any`: the specification of cost functional to be used (default: 1.0, i.e., 1-norm)
  * `flatten::Any`: the method for flattening vector-valued data to scalar-valued data (default: 1.0, i.e., 1-norm)

### Output Arguments

  * `dvec::Matrix{Float64}`: the vector of expansion coefficients corresponding to the best basis
  * `BS::BasisSpec`: a BasisSpec object which specifies the best basis
