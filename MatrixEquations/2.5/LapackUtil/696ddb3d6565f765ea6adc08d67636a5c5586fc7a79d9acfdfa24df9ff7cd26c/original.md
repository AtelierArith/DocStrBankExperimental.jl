```
lag2(A, B, SAFMIN) -> (SCALE1, SCALE2, WR1, WR2, WI)
```

Compute the eigenvalues of a 2-by-2 generalized real eigenvalue problem for the matrix pair `(A,B)`, with scaling as necessary to avoid over-/underflow. `SAFMIN` is the smallest positive number s.t. `1/SAFMIN` does not overflow. If `WI = 0`, `WR1/SCALE1` and `WR2/SCALE2` are the resulting real eigenvalues, while if `WI <> 0`, then `(WR1+/-im*WI)/SCALE1` are the resulting complex eigenvalues. Interface to the LAPACK subroutines DLAG2/SLAG2.
