function HGLET*GHWT*BestBasis(GP::GraphPart;      dmatrixH::Array{Float64,3} = Array{Float64,3}(undef,0,0,0),     dmatrixHrw::Array{Float64,3} = Array{Float64,3}(undef,0,0,0),      dmatrixHsym::Array{Float64,3} = Array{Float64,3}(undef,0,0,0),     dmatrixG::Array{Float64,3} = Array{Float64,3}(undef,0,0,0),      cfspec::Any = 0.1,flatten::Any = 1)

```
Select the best basis from several matrices of expansion coefficients
```

### Input Arguments

  * `dmatrixH`:    the matrix of HGLET expansion coefficients ==> eigenvectors of L
  * `dmatrixHrw`:  the matrix of HGLET expansion coefficients ==> eigenvectors of Lrw
  * `dmatrixHsym`: the matrix of HGLET expansion coefficients ==> eigenvectors of Lsym
  * `dmatrixG`:    the matrix of GHWT expansion coefficients
  * `GP`:          a GraphPart object
  * `cfspec`: the cost functional specification to be used: see utils.jl   for the detail. If it's a number, say, p, then the l^p norm is used.   If it's a function, then that function is used. Default is 0.1, i.e., l^0.1
  * `flatten`: the method for flattening vector-valued data to scalar-valued data;   If it's a number, say, p, then the sum of the l^p norm is computed.   There are many other options, such as :ash, :entropy, etc. See utils.jl   for the detail. Default is 1, i.e, the sum of the l^1 norm of the coefs.

### Output Argument

  * `dvec`:     the vector of expansion coefficients corresponding to the bestbasis
  * `BS`:       a BasisSpec object which specifies the best basis
  * `trans`:    specifies which transform was used for that portion of the signal:   00 = HGLET with L   01 = HGLET with Lrw   10 = HGLET with Lsym   11 = GHWT
