function HGLET_jkl(GP::GraphPart, drow::Int, dcol::Int)

```
Generate the (j,k,l) indices for the HGLET basis vector corresponding to
    the coefficient dmatrix(drow,dcol)
```

### Input Arguments

  * `GP`:    a GraphPart object
  * `drow`:  the row of the expansion coefficient
  * `dcol`:  the column of the expansion coefficient

### Output Argument

  * `j`: the level index of the expansion coefficient
  * `k`: the subregion index of the expansion coefficient
  * `l`: the eigenvector index of the expansion coefficient
