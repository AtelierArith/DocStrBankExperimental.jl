```
mat_center(X; mat = "her")
```

This function centers input.  If X is a Hermitian matrix, then $Xcen = X - Tr(X)/N*I$`. If X is a rectangular matrix, then``Xcen = X - X*ones(M,1)*ones(1,M)/M``.

# Arguments

  * `X`: a Hermitian or rectangular matrix
  * `mat`: the type of `X`, valid options are "her" and "rec"

# Outputs:

  * `Xc`: centered version of `X`
