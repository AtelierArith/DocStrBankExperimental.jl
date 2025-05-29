```
(dvecf2c, BSf2c) = ghwt_f2c_bestbasis(dmatrix::Array{Float64,3}, GP::GraphPart;
                                      cfspec::Any = 1.0, flatten::Any = 1.0,
                                      j_start::Int = 1, j_end::Int = size(dmatrix,2),
                                      useParent::Bool = true)
```

Select the fine-to-coarse best basis from the matrix of GHWT expansion coefficients

### Input Arguments

  * `dmatrix::Array{Float64,3}`: the matrix of expansion coefficients
  * `GP::GraphPart`: an input GraphPart object
  * `cfspec::Any`: the specification of cost functional to be used (default: 1.0, i.e., 1-norm)
  * `flatten::Any`: the method for flattening vector-valued data to scalar-valued data (default: 1.0, i.e., 1-norm)
  * `useParent::Bool`: the flag to indicate if we update the selected best basis   subspace to the parent when parent and child have the same cost (default = true)

### Output Arguments

  * `dvecf2c::Matrix{Float64}`: the vector of expansion coefficients corresponding to the fine-to-coarse best basis
  * `BSf2c::BasisSpec`: a BasisSpec object which specifies the fine-to-coarse best basis
