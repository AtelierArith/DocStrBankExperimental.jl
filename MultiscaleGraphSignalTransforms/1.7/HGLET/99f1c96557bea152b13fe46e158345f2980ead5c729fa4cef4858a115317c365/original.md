function HGLET*Analysis*All(G::GraphSig, GP::GraphPart)

```
For a GraphSig object 'G', generate the 3 matrices of HGLET expansion 
coefficients corresponding to the eigenvectors of L, Lrw and Lsym
```

### Input Arguments

  * `G`:  a GraphSig object
  * `GP`: a GraphPart object

### Output Argument

  * `dmatrixH`:        the matrix of expansion coefficients for L
  * `dmatrixHrw`:      the matrix of expansion coefficients for Lrw
  * `dmatrixHsym`:     the matrix of expansion coefficients for Lsym
