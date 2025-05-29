```
Bbasis, infovec = ghwt_tf_bestbasis_2d(dmatrix::Matrix{Float64},GProws::GraphPart,GPcols::GraphPart)
```

Implementation of 2d time-frequency adapted GHWT method. Modified from the idea in paper "Image compression with adaptive Haar-Walsh tilings" by Maj Lindberg and Lars F. Villemoes.

### Input Arguments

  * `dmatrix`: The ghwt expanding coefficients of matrix on all levels contatenated in a 2d matrix.
  * `GProws`: Corresponding to the affinity matrix on rows.
  * `GPcols`: Corresponding to the affinity matrix on cols.

### Output Arguments

  * `Bbasis`: The coefficients of the best-basis.
  * `infovec`: [infovec[i,1],infovec[i,2]] is the location of Bbasis[i] in dmatrix.

Copyright 2018 The Regents of the University of California

Implemented by Yiqun Shao (Adviser: Dr. Naoki Saito)
