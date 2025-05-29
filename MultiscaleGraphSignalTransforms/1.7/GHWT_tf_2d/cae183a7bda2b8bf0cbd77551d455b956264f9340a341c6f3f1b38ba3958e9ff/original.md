```
matrix = ghwt_tf_synthesis_2d(dmatrix::Matrix{Float64}, GProws::GraphPart, GPcols::GraphPart)
```

Synthesis the matrix from the coefficients of selected basis vectors.

### Input Arguments

  * `dmatrix`: Only selected basis vectors are nonzero with expanding coeffcients.
  * `GProws`: Corresponding to the affinity matrix on rows.
  * `GPcols`: Corresponding to the affinity matrix on cols.

### Output Arguments

  * `matrix`: Synthesized matrix

Copyright 2018 The Regents of the University of California

Implemented by Yiqun Shao (Adviser: Dr. Naoki Saito)
