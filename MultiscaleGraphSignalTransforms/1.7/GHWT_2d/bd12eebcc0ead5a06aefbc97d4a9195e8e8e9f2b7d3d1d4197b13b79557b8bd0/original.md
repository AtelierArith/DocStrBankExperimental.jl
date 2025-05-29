```
dvec, BSrows, BScols = ghwt_2d_bestbasis(matrix::Array{Float64,2},GProws::GraphPart,GPcols::GraphPart,
costfun_rows::Any = 1.0, costfun_cols::Any = 1.0, flatten_rows::Any = 1.0, flatten_cols::Any = 1.0)
```

For a matrix, equipped with row and column weight recursive partitionings and weight matrices, generate the (non-redundant) matrix of GHWT expansion coefficients, using the best basis algorithm to select best bases for the rows and columns

### Input Argument

  * `matrix`              the matrix to be analyzed
  * `GProws`              the recursive partitioning on the rows
  * `GPcols`              the recursive partitioning on the columns
  * `costfun_rows`        the cost functional to be used for the rows
  * `costfun_cols`        the cost functional to be used for the columns
  * `flatten_rows`        the method for flattening vector-valued data to scalar-valued data for the rows
  * `flatten_cols`        the method for flattening vector-valued data to scalar-valued data for the columns

### Output Argument

  * `dvec`                the GHWT expansion coefficients (not redundant)
  * `BSrows`              the best basis on the rows
  * `BScols`              the best basis on the columns

Copyright 2019 The Regents of the University of California

Implemented by Yiqun Shao (Adviser: Dr. Naoki Saito)
