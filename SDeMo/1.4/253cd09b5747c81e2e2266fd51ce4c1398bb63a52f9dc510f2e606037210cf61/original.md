```
kfold(y, X; k = 10, permute = true)
```

Returns splits of the data in which 1 group is used for validation, and `k`-1 groups are used for training. All `k``groups have the (approximate) same size, and each instance is only used once for validation (and`k`-1 times for training). The groups are stratified (so that they have the same prevalence).

This method returns a vector of tuples, with each entry have the training data first, and the validation data second.
