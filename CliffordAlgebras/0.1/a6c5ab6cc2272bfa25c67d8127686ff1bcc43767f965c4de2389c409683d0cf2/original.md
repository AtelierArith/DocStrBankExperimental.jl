```
dual(mv::MultiVector)
```

Returns the Poincaré dual of the MultiVector, such that for all basis MultiVectors mv * dual(mv) = pseudoscalar. Dual is a linear map and the images of other MultiVectors follow from the images of the basis MultiVectors.
