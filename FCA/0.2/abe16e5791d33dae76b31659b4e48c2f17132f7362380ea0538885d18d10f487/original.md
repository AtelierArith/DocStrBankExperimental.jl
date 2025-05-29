```
icf(Z; opt = "orth")
```

Apply independent component analysis to Z, return estimated  mixing matrix and independent components

# Arguments

  * `Z`: an array of vectors of the same length, represent the      realizations of mixed independent signals
  * `obj`: the type of loss function, valid options are "kurt" and "ent"
  * `opt`: string, type of optimization, valid option: "orth", "sphe".        The "sphe" is only designed for "kurt" loss function

# Outputs

  * `Aest`: estimated mixing matrix of size `s`-by-`s`, where `s` = size(Z,1)
  * `Xest`: estimated independent component `Xest = pinv(Aest)*Z`
