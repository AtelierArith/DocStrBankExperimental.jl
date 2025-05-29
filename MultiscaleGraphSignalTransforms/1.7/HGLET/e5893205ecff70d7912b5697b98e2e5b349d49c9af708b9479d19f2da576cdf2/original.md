function HGLET*GHWT*BestBasis_minrelerror(GP::GraphPart, G::GraphSig;     dmatrixH::Array{Float64,3} = Array{Float64,3}(undef,0,0,0),      dmatrixHrw::Array{Float64,3} = Array{Float64,3}(undef,0,0,0),     dmatrixHsym::Array{Float64,3} = Array{Float64,3}(undef,0,0,0),     dmatrixG::Array{Float64,3} = Array{Float64,3}(undef,0,0,0),      compare::Bool = true)

```
Find the best basis for approximating the signal 'G' by performing the 
    best basis search with a range of tau-measures as cost functionals
    (tau = 0.1,0.2,...,1.9) and minimizing the relative error.
```

### Input argument:

  * `dmatrixH`: the matrix of HGLET expansion coefficients ==> eigenvectors of L
  * `dmatrixHrw`: the matrix of HGLET expansion coefficients ==> eigenvectors of Lrw
  * `dmatrixHsym`: the matrix of HGLET expansion coefficients ==> eigenvectors of Lsym
  * `dmatrixG`: the matrix of GHWT expansion coefficients
  * `GP`: a GraphPart object
  * `G`: the GraphSig object
  * `compare`: if it is false, don't compare the hybrid best basis to the GHWT fine-to-coarse best basis

### Output argument:

  * `dvec`: the vector of expansion coefficients corresponding to the bestbasis
  * `BS`: a BasisSpec object which specifies the best basis
  * `trans`: specifies which transform was used for that portion of the signal   00 = HGLET with L   01 = HGLET with Lrw   10 = HGLET with Lsym   11 = GHWT
  * `tau`: the tau that yields the smallest relative error
