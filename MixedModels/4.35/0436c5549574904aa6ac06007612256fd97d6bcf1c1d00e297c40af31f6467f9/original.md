```
VarCorr
```

Information from the fitted random-effects variance-covariance matrices.

# Members

  * `σρ`: a `NamedTuple` of `NamedTuple`s as returned from `σρs`
  * `s`: the estimate of the per-observation dispersion parameter

The main purpose of defining this type is to isolate the logic in the show method.
