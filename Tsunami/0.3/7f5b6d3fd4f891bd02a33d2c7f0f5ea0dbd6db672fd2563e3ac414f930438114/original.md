```
accuracy(ŷ::AbstractMatrix, y)
```

Compute the classification accuracy of a batch of predictions `ŷ` against true labels `y`. `y` can be either a vector or a matrix.  If `y` is a vector, it is assumed that the labels are integers in the range `1:K`  where `K == size(ŷ, 1)` is the number of classes.
