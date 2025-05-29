```
FI_Expt(y1, y2, dx; ftype=:norm)
```

Calculate the classical Fisher information (CFI) based on the experiment data.

  * `y1`: Experimental data obtained at the truth value (x).
  * `y1`: Experimental data obtained at x+dx.
  * `dx`: A known small drift of the parameter.
  * `ftype`: The distribution the data follows. Options are: norm, gamma, rayleigh, and poisson.
