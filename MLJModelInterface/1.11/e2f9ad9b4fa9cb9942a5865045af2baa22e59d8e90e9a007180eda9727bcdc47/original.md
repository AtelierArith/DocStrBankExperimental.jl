```
MLJModelInterface.fit(model, verbosity, data...) -> fitresult, cache, report
```

All models must implement a `fit` method. Here `data` is the output of `reformat` on user-provided data, or some some resampling thereof. The fallback of `reformat` returns the user-provided data (eg, a table).
