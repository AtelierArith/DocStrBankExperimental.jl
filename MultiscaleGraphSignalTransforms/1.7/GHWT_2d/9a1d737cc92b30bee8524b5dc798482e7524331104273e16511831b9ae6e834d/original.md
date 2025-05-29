```
dmatrix = ghwt_analysis_2d(matrix::Array{Float64,2}, GProws::GraphPart, GPcols::GraphPart)
```

For a matrix, equipped with row and column weight recursive partitionings and weight matrices, generate the redundant matrix of GHWT expansion coefficients.

### Input Arguments

`matrix`              the matrix to be analyzed    `GProws`              the recursive partitioning on the rows    `GPcols`              the recursive partitioning on the columns

### Output Arguments

`dmatrix`                the GHWT dictionary expansion coefficients

Copyright 2019 The Regents of the University of California

Implemented by Yiqun Shao (Adviser: Dr. Naoki Saito)
