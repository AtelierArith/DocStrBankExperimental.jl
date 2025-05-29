```
GeneralizedRankRevealing <: Factorization
```

Matrix factorization type for the Generalized Rank Reveling decomposition of two matrices `A` and `B` with the same number of columns. This is obtained via the function `grr(A,B)`.

By calling `d_+` the dimension of the sum of `A` and `B` row spaces, this factorization has the decomposes the matrices as

```
                | I 0 0 |
| A | = | X 0 | | 0 0 I |
| B |   | 0 Y | | 0 I 0 | H
                | 0 0 I |
```

| Component | Description                         |
|:--------- |:----------------------------------- |
| `F.X`     | `m_A x r_A` full column rank matrix |
| `F.Y`     | `m_B x r_B` full column rank matrix |
| `F.H`     | `d_+ x n` full row rank matrix      |

Other useful fields are:

  * `F.r1`: Rank of `A` minus minus the intersection
  * `F.r2`: Rank of `B` minus minus the intersection
  * `F.r3`: Rank of the intersection
