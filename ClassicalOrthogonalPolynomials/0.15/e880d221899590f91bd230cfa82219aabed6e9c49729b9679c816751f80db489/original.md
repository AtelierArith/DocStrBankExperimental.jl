```
jacobimatrix(P)
```

returns the Jacobi matrix `X` associated to a quasi-matrix of orthogonal polynomials satisfying

```julia
x = axes(P,1)
x*P == P*X
```

Note that `X` is the transpose of the usual definition of the Jacobi matrix.
