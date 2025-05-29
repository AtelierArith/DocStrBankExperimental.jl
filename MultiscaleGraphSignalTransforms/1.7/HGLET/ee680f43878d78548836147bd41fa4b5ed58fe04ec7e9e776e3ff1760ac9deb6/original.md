function HGLET_Analysis(G::GraphSig, GP::GraphPart, gltype::Symbol = :L)

```
For a GraphSig object 'G', generate the matrix of HGLET expansion
coefficients corresponding to the eigenvectors of specified version of
the graph Laplacian matrix, i.e., either L, Lrw, or Lsym
```

### Input Arguments

  * `G`:  a GraphSig object
  * `GP`: a GraphPart object
  * `gltype`: :L, :Lrw, or :Lsym, indicating which eigenvectors are used

### Output Argument

  * `dmatrix`: the matrix of expansion coefficients using the specific GL matrix
