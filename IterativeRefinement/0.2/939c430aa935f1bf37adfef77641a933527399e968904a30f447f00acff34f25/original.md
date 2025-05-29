```
equilibrators(A) -> R,C
```

compute row- and column-wise scaling vectors `R,C` for a matrix `A` such that the absolute value of the largest element in any row or column of `Diagonal(R)*A*Diagonal(C)` is close to unity. Designed to reduce the condition number of the working matrix.
