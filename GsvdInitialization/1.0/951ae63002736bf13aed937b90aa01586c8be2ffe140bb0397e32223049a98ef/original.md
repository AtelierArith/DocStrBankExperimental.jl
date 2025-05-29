```
Wadd, Hadd, S = gsvdrecover(X, W0, H0, kadd, f)
```

Augment components for `W` and `H` without polishing by NMF.

Outputs:

`Wadd`: augmented NMF solution

`Hadd`: augmented NMF solution

`S`: generalized singular values for the `kadd` augmented components

Arguments:

`X`: non-nagetive 2D data matrix

`W0`: NMF solution

`H0`: NMF solution

`kadd`: number of new components

`f`: SVD (or Truncated SVD) of `X`
