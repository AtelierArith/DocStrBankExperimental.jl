```
IndAffine(A, b; iterative=false)
```

If `A` is a matrix (dense or sparse) and `b` is a vector, return the indicator function of the affine set

$$
S = \{x : Ax = b\}.
$$

If `A` is a vector and `b` is a scalar, return the indicator function of the set

$$
S = \{x : \langle A, x \rangle = b\}.
$$

By default, a direct method (QR factorization of matrix `A'`) is used to evaluate `prox!`. If `iterative=true`, then `prox!` is evaluated approximately using an iterative method instead.
