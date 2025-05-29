```
freecf(Z; mat="her", obj="kurt", opt="orth")
```

Apply free component analysis to Z, return estimated mixing matrix and free components

# Arguments

  * `Z`: an array of matrices of mat and of the same dimensions
  * `mat`: the type of Z[i], valid options are "her" and "rec"
  * `obj`: the type of loss function, valid options are "kurt" and "ent"
  * `opt`: string, type of optimization, valid option: "orth", "sphe"

# Outputs

  * `Aest`: a matrix of size `s`-by-`s`, where `s` = size(Z, 1)
  * `Xest`: an array of "free" matrices, such that `Z = Aest*Xest`
