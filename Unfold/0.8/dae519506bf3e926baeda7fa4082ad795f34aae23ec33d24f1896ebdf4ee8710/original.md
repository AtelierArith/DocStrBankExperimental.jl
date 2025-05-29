```
modelmatrix(uf::UnfoldLinearModel)
```

returns the modelmatrix of the model. Concatenates them, except in the MassUnivariate cases, where a vector of modelmatrices is return

Compare with `modelmatrices` which returns a vector of modelmatrices, one per event
