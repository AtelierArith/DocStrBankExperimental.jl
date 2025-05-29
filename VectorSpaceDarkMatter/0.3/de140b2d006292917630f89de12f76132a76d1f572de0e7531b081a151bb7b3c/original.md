```
readK(infile[, vmax, qmax]; use_err=true)
```

Reads partial rate matrix from `infile`. Can optionally manually define the  basis maximums via `vmax` and `qmax` arguments, otherwise will attempt to read from the header of the csv file.

`use_err` : Whether or not to load the uncertainties.
