```
top2latentdims(dbm, x)
```

Get a two-dimensional representation for all the samples/rows in the data set `x`, employing a given `dbm` for the dimension reduction. For achieving the dimension reduction, at first the mean-field activation induced by the samples in the hidden nodes of the last/top hidden layer of the `dbm` is calculated. The mean-field activation of the top hidden nodes is logit-transformed to get a better separation. If the number of hidden nodes in the last hidden layer is greater than 2, a principal component analysis (PCA) is used on these logit-transformed mean-field values to obtain a two-dimensional representation. The result is a matrix with 2 columns, each row belonging to a sample/row in `x`.
