```
saloc2(A, B, evc, tola, tolb) -> (F, U)
```

Compute for the real pair `(A,B)` with `A` of order two, a matrix `F` such that the eigenvalues  of the matrix `A+B*F` are equal to the complex conjugate pair contained in `evc`.  The absolute thresholds `tola` and `tolb` for the nonzero elements in `A` and `B`, respectively,  are used for controllability checks.

If the pair `(A,B)` is uncontrollable, then `F = nothing` and `U` contains an orthogonal transformation  matrix such that the transformed pair `(U'*A*U, U'*B)` is in the form

```
                 [ A1  X    B1 ]
[ U'*A*U U'*B] = [             ] ,
                 [  0  A2   0  ]
```

where the pair `(A1,B1)` is controllable. If `norm(B) < tolb`, then `U` is the `2x2` identity matrix.
