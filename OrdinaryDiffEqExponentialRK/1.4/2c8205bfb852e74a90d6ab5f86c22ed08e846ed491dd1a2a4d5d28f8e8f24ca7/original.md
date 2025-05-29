```julia
Exprb32(; m = 30,
          iop = 0)
```

Semilinear ODE solver 3rd order adaptive Exponential-Rosenbrock scheme.

### Keyword Arguments

  * `m`: Controls the size of Krylov subspace.
  * `iop`: If not zero, determines the length of the incomplete orthogonalization procedure (IOP).   Note that if the linear operator/Jacobian is hermitian, then the Lanczos algorithm will always be used and the IOP setting is ignored.

## References

Hochbruck, M., & Ostermann, A. (2010). Exponential integrators. Acta Numerica, 19, 209-286. (https://doi.org/10.1017/S0962492910000048)
