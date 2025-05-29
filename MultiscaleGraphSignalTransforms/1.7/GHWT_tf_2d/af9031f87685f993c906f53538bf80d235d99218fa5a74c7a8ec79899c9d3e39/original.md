```
dmatrix = ghwt_tf_init_2d(matrix::Matrix{Float64}, GProws::GraphPart, GPcols::GraphPart)

Partition matrix first to get GProws and GPcols. Then expand matrix
in two directions to get dmatrix
```

### Input Arguments

  * `matrix::Matrix{Float64}`: an input matrix
  * `GProws::GraphPart`: partitioning using rows as samples
  * `GPcols::GraphPart`: partitioning using cols as samples

### Output Argument

  * `dmatrix::matrix{Float64}`: expansion coefficients of matrix
