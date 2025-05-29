```
WSVarLmmModel
```

Within-subject variance linear mixed model, which contains a vector of  `WSVarLmmObs` as data, model parameters, and working arrays.

```
WSVarLmmModel(obsvec; obswts, meannames, renames, wsvarnames)
```

# Positional arguments

  * `obsvec`: Vector of WSVarLmmObs

# Keyword arguments

  * `obswts`: Subject-level weight vector of observation weights, length of the `obsvec` object.
  * `meannames`: Names of the mean fixed effects covariates
  * `renames`: Names of the random location effects covariates
  * `wsvarnames`: Names of the ws variance fixed effects covariates
