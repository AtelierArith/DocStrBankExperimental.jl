```
(dvec_ngwp, BS_ngwp) = ngwp_bestbasis(dmatrix::Array{Float64,3}, GP_star::GraphPart;
                                      cfspec::Any = 1.0, flatten::Any = 1.0,
                                      j_start::Int = 1, j_end::Int = size(dmatrix, 2),
                                      useParent::Bool = true)
```

Select the best basis from the matrix of NGWP expansion coefficients.

# Input Arguments

  * `dmatrix::Array{Float64,3}`: the matrix of expansion coefficients
  * `GP_star::GraphPart`: an input GraphPart object of the dual graph
  * `cfspec::Any`: the specification of cost functional to be used (default = 1.0,   i.e., 1-norm)
  * `flatten::Any`: the method for flattening vector-valued data to scalar-valued   data (default = 1.0, i.e, 1-norm)
  * `useParent::Bool`: the flag to indicate if we update the selected best basis   subspace to the parent when parent and child have the same cost (default = false)

# Output Arguments

  * `dvec_ngwp::Matrix{Float64}`: the vector of expansion coefficients corresponding   to the NGWP best basis
  * `BS_ngwp::BasisSpec`: a BasisSpec object which specifies the NGWP best basis
