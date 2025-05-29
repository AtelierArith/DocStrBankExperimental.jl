```
AnovaResult{M, T, N}
```

Returned object of `anova`.

  * `M` is a subtype of `Tuple` if multiple models are provided; otherwise, a typeof model.
  * `T` is a subtype of `GoodnessOfFit`; either `FTest` or `LRT`.
  * `N` is the length of parameters.

## Fields

  * `model`: full model or tuple of tested models.
  * `type`: type of `anova`.
  * `dof`: degree of freedoms of models or factors.
  * `deviance`: deviance(s) for calculating test statistics. See `deviance` for more details.
  * `teststat`: value(s) of test statiscics.
  * `pval`: p-value(s) of test statiscics.
  * `tests`: `NamedTuple` contained extra statistics.
