```
decompress_symmetric
```

For example:      a 3*3 positive semidefinite matrix:      `[  a       b       d;          b       c       e;          d       e       f       ]`      represents by:      `[  x_D[1]  x_L[3]  x_L[2];          x_L[1]  x_D[2]  x_L[1];          x_L[2]  x_L[3]  x_D[3]  ]`

  * `x_L::AbstractArray`: representing lower triangular part of a `n*n` matrix, length should be `(n^2-n)÷2`
  * `x_D::AbstractArray`: representing diagonal part of a `n*n` matrix, length should be `n`
