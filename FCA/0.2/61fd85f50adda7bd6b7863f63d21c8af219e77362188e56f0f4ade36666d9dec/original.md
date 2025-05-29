```
mat_embed(X, dim; zero_pos = -1, tpin = "her", tpout = "her")
```

This function embeds X into new dimensions dim, with the Cartesian order of the entries are preserved. Fill in zeros at zero_pos if necessary.  

# Arguments

  * `X`: a Hermitian or rectangular matrice
  * `dim`: target dimension, array-like [Nnew,Mnew]
  * `zero_pos`: an array of user specify Cartesian position for zeros. if               it is -1, then use randomly generated position.
  * `tpin`: the type of input matrix, valid options are "her" and "rec".
  * `tpout`: the type of ouput matrix, valid options are "her" and "rec"

# Outputs

  * `Xnew`: a matrix of dimension dim and the type tpin. The entries          Xnew are from X, with possible extra zeros at zero_pos,
