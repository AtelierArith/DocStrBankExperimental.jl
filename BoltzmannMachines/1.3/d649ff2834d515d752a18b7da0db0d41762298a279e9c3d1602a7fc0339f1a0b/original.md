```
crossvalidation(x, monitoredfit; ...)
```

Performs k-fold cross-validation, given

  * the data set `x` and
  * `monitoredfit`: a function that fits and evaluates a model. As arguments it must accept:

      * a training data data set
      * a `DataDict` containing the evaluation data.

The return values of the calls to the `monitoredfit` function are concatenated with `vcat`. If the monitoredfit function returns `Monitor` objects, `crossvalidation` returns a combined `Monitor` object that can be displayed by creating a cross-validation plot via `BoltzmannMachinesPlots.crossvalidationplot`.

# Optional named argument:

  * `kfold`: specifies the `k` in "`k`-fold" (defaults to 10).

    crossvalidation(x, monitoredfit, pars; ...)

If additionaly a vector of parameters `pars` is given, `monitoredfit` also expects an additional parameter from the parameter set.
