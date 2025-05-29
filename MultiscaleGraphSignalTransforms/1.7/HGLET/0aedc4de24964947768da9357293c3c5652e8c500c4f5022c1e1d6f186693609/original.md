function HGLET_BestBasis(GP::GraphPart;      dmatrix::Array{Float64,3} = Array{Float64,3}(undef,0,0,0),     gltype::Symbol = :L, cfspec::Any = 0.1, flatten::Any = 1)

```
Select the HGLET best basis from the input matrix of expansion coefficients
```

### Input Arguments

  * `GP`:      a GraphPart object
  * `dmatrix`: the matrix of HGLET expansion coefficients
  * `gltype`:  the type of graph Laplacian matrix used for HGLET dictionary   (default = :L)
  * `cfspec`: the cost functional specification to be used: see utils.jl   for the detail. If it's a number, say, p, then the l^p norm is used.   If it's a function, then that function is used. Default is 0.1, i.e., l^0.1
  * `flatten`: the method for flattening vector-valued data to scalar-valued data;   If it's a number, say, p, then the sum of the l^p norm is computed.   There are many other options, such as :ash, :entropy, etc. See utils.jl   for the detail. Default is 1, i.e, the sum of the l^1 norm of the coefs.

### Output Argument

  * `dvec`: the vector of expansion coefficients corresponding to the bestbasis
  * `BS`:   a BasisSpec object which specifies the best basis
