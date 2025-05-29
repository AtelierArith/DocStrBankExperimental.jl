```
function LPHGLET_Analysis_All(G::GraphSig, GP::GraphPart; ϵ::Float64 = 0.3)
```

For a GraphSig object 'G', generate the 2 matrices of Lapped-HGLET expansion coefficients corresponding to the eigenvectors of L and Lsym

### Input Arguments

  * `G`:  a GraphSig object
  * `GP`: a GraphPart object
  * `ϵ`: relative action bandwidth (default: 0.3)

### Output Argument

  * `dmatrixlH`:        the matrix of expansion coefficients for L
  * `dmatrixlHsym`:     the matrix of expansion coefficients for Lsym
  * `GP`:              a GraphPart object
