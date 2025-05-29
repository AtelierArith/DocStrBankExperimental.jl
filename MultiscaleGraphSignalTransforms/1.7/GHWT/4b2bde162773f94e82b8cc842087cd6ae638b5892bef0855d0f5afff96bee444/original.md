```
(dvecc2f, BSc2f) = ghwt_c2f_bestbasis(dmatrix::Array{Float64,3}, GP::GraphPart;
                                      cfspec::Any = 1.0, flatten::Any = 1.0,
                                      j_start::Int = 1, j_end::Int = size(dmatrix,2),
                                      useParent::Bool = true)
```

Select the coarse-to-fine best basis from the matrix of GHWT expansion coefficients

### Input Arguments

  * `dmatrix::Array{Float64,3}`: the matrix of expansion coefficients
  * `GP::GraphPart`: an input GraphPart object
  * `cfspec::Any`: the specification of cost functional to be used (default = 1.0, i.e., 1-norm)
  * `flatten::Any`: the method for flattening vector-valued data to scalar-valued data (default = 1.0, i.e, 1-norm)
  * `useParent::Bool`: the flag to indicate if we update the selected best basis   subspace to the parent when parent and child have the same cost (default = true)

### Output Arguments

  * `dvecc2f::Matrix{Float64}`: the vector of expansion coefficients corresponding to the coarse-to-fine best basis
  * `BSc2f::BasisSpec`: a BasisSpec object which specifies the coarse-to-fine best basis
