```
grr(A, B) -> GeneralizedRankRevealing
```

Compute the Generalized LU decomposition of matrices `A` and `B`. There are matrices `X`, `Y` and `H` such that

```
                | I 0 0 |
| A | = | X 0 | | 0 0 I |
| B |   | 0 Y | | 0 I 0 | H
                | 0 0 I |
```
