```
PCATransform
```

The PCA transform will project the model features, which also serves as a way to decrease the dimensionality of the problem. Note that this method will only use the training instances, and unless the `absences=true` keyword is used, only the present cases. This ensure that there is no data leak (neither validation data nor the data from the raster are used).

This is an alias for `MultivariateTransform{PCA}`.
