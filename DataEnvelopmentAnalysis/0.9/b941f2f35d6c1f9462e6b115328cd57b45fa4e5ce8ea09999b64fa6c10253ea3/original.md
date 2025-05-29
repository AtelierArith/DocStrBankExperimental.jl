```
deaenv(X, Y, B; Gx, Gy, Gb)
```

Compute data envelopment analysis environmental model for inputs `X`, good outputs `Y`, and bad outputs `B`, using directions `Gx`, `Gy`, and `Gb`.

# Direction specification:

The directions `Gx`, `Gy`, and `Gb` can be one of the following symbols.

  * `:Zeros`: use zeros.
  * `:Ones`: use ones.
  * `:Observed`: use observed values.
  * `:Mean`: use column means.

Alternatively, a vector or matrix with the desired directions can be supplied.

# Optional Arguments

  * `slack=true`: computes input and output slacks.
  * `Xref=X`: Identifies the reference set of inputs against which the units are evaluated.
  * `Yref=Y`: Identifies the reference set of good outputs against which the units are evaluated.
  * `Bref=B`: Identifies the reference set of bad outputs against which the units are evaluated.
  * `names`: a vector of strings with the names of the decision making units.
