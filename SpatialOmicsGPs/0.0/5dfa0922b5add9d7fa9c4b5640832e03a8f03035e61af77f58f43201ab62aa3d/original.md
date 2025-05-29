```
spatialde_varpars_opt(lσ²s, lδs, minus_loglikes)
```

Compute the optimal spatial variance parameters and length scale index for all variables by finding for each row the minimum of the negative log-likelihood in `minus_loglikes` and returning the corresponding variance parameters and length scale index.  The input `lσ²s` and `lδs` should be matrices with the same number of rows as `minus_loglikes` and the same number of columns as the length scales used in the optimization.
