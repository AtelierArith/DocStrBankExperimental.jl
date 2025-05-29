```
malmluen(X, Y, B; Gx, Gy, Gb)
```

Compute the Malmquist-Luenberger productivity index using data envelopment analysis for inputs `X`,  good outputs `Y`, and bad outputs `B`, using directions `Gx`, `Gy`, and `Gb`.

# Direction specification:

The directions `Gx`, `Gy`, and `Gb` can be one of the following symbols.

  * `:Zeros`: use zeros.
  * `:Ones`: use ones.
  * `:Observed`: use observed values.
  * `:Mean`: use column means.

# Optional Arguments

  * `refperiod=:Geomean`: chooses reference period for technological change: `:Base`, `:Comparison` or `:Geomean`.
  * `names`: a vector of strings with the names of the decision making units.
