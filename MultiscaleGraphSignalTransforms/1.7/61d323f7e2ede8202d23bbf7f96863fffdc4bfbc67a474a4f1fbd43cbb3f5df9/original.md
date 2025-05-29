```
function NGWP_jkl(GP_star::GraphPart, drow::Int, dcol::Int)
```

Generate the (j,k,l) indices for the NGWP basis vector corresponding to the coefficient dmatrix(drow,dcol)

### Input Arguments

  * `GP_star::GraphPart`: a GraphPart object of the dual grpah
  * `drow::Int`: the row of the expansion coefficient
  * `dcol::Int`: the column of the expansion coefficient

### Output Argument

  * `j`: the level index of the expansion coefficient
  * `k`: the subregion in dual graph's index of the expansion coefficient
  * `l`: the tag of the expansion coefficient
