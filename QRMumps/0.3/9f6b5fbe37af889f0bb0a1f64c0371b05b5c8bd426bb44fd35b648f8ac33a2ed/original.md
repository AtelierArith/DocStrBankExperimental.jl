```
qrm_vecnrm!(x, nrm; ntype='2')
```

This routine computes the one-norm $\|x\|_1$, the infinity-norm $\|x\|_{\infty}$ or the two-norm $\|x\|_2$ of a vector.

#### Input Arguments :

  * `x`: the x vector(s).
  * `nrm`: the computed norm(s). If x is a matrix this argument has to be a vector and each of its elements will contain the norm of the corresponding column of x.
  * `ntype`: the type of norm to be computed. It can be either `'i'`, `'1'` or `'2'` for the infinity, one and two norms, respectively.
