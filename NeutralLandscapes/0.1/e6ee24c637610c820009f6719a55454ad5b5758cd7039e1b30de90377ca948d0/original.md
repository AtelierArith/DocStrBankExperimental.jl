```
label(mat[, neighborhood = :rook])
```

Assign an arbitrary label to all clusters of contiguous matrix elements with the same value. Returns a matrix of values and the total number of final clusters. The `neighborhood` structure can be  `:rook`     `:queen`    `:diagonal`  0 1 0        1 1 1        0 1 1  1 x 1        1 x 1        1 x 1  0 1 0        1 1 1        1 1 0  `:rook` is the default
