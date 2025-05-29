```
dmatrix, GProws, GPcols = ghwt_tf_init_2d(matrix::Matrix{Float64})

Partition matrix first to get GProws and GPcols. Then expand matrix
in two directions to get dmatrix
```

### Input Arguments

  * `matrix::Matrix{Float64}`: an input matrix

### Output Argument

  * `GProws::GraphPart`: partitioning using rows as samples
  * `GPcols::GraphPart`: partitioning using cols as samples
  * `dmatrix::matrix{Float64}`: expansion coefficients of matrix
