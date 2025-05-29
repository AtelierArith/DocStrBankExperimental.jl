```
decompress_symmetric
```

例えば:      3*3 の正定値半行列:      `[  a       b       d;          b       c       e;          d       e       f       ]`      は次のように表されます:      `[  x_D[1]  x_L[3]  x_L[2];          x_L[1]  x_D[2]  x_L[1];          x_L[2]  x_L[3]  x_D[3]  ]`

  * `x_L::AbstractArray`: `n*n` 行列の下三角部分を表し、長さは `(n^2-n)÷2` である必要があります
  * `x_D::AbstractArray`: `n*n` 行列の対角部分を表し、長さは `n` である必要があります
