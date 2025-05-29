```
decompose(σ :: Series{C,M}, rkf :: Function)
```

Decompose the series $σ$ as a weighted sum of exponentials. Return $ω$, $Ξ$ where

  * $ω$ is the vector of weights,
  * $Ξ$ is the matrix of frequency points, stored per row.

The list of monomials of degree $\leq {d-1 \over 2}$ are used to construct the Hankel matrix, where $d$ is the maximal degree of the moments in $σ$.

The optional argument `rkf` is the rank function used to determine the numerical rank from the vector S of singular values. Its default value `eps_rkf(1.e-6)` determines the rank as the first i s.t. S[i+1]/S[i]< 1.e-6 where S is the vector of singular values.

If the rank function cst_rkf(r) is used, the SVD is truncated at rank r.
