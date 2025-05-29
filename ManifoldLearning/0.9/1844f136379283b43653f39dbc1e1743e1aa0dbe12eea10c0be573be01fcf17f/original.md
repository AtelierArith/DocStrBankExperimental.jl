```
predict(R::NonlinearDimensionalityReduction)
```

Returns a reduced space representation of the data given the model `R` inform of  the projection matrix (of size $(d, n)$), where `d` is a dimension of the reduced space and `n` in the number of the observations. Each column of the projection matrix corresponds to an observation in projected reduced space.
