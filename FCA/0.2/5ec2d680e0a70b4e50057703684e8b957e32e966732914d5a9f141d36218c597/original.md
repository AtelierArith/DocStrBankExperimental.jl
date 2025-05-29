```
free_whiten(Z; mat = "her")
```

This function whitens input array of matrices in the free probability sense

# Arguments

  * `Z`: an array of matrices of mat and of the same dimensions
  * `mat`: the type of Z[i], valid options are "her" and "rec"

# Outputs

  * `Y`: an array of centered matrices, whitened in the free probability sense,       that is, Tr(Y[i]*Y[j]')/size(Y[1],1) = (i == j)
  * `U`: a matrix of size s-by-s, where s = size(Z, 1)
  * `Σ`: a matrix of size s-by-s,
