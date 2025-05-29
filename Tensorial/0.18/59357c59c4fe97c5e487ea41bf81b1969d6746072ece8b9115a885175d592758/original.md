```
@Tensor [a b; c d]
@Tensor [[a, b];[c, d]]
@Tensor [i+j for i in 1:2, j in 1:2]
@Tensor ones(2, 2, 2)
```

A convenient macro to construct `Tensor` with arbitrary dimension.
