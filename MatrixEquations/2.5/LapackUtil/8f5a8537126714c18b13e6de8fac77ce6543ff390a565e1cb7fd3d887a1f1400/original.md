```
trsyl3!(transa, transb, A, B, C, isgn=1) -> (C, scale)
```

Solves the Sylvester matrix equation `A * X +/- X * B = scale*C` where `A` and `B` are both quasi-upper triangular. If `transa = N`, `A` is not modified. If `transa = T`, `A` is transposed. If `transa = C`, `A` is conjugate transposed. Similarly for `transb` and `B`. If `isgn = 1`, the equation `A * X + X * B = scale * C` is solved. If `isgn = -1`, the equation `A * X - X * B = scale * C` is solved.

Returns `X` (overwriting `C`) and `scale`.

The block-algorithm of [1] and [2] is used. 

References: [1] E. S. Quintana-Orti and R. A. Van De Geijn (2003). Formal derivation of     algorithms: The triangular Sylvester equation, ACM Transactions     on Mathematical Software (TOMS), volume 29, pages 218-243.

[2] A. Schwarz and C. C. Kjelgaard Mikkelsen (2020). Robust Task-Parallel     Solution of the Triangular Sylvester Equation. Lecture Notes in     Computer Science, vol 12043, pages 82-92, Springer.
