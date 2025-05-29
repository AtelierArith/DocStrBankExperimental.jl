```julia
CG3(; krylov = false,
      m = 30,
      iop = 0)
```

Semilinear ODE solver Third order Crouch-Grossman method.

### Keyword Arguments

  * `krylov`: Determines whether Krylov approximation or operator caching is used, the latter only available for semilinear problems.   `krylov=true` is much faster for larger systems and is thus recommended whenever there are >100 ODEs.
  * `m`: Controls the size of Krylov subspace.
  * `iop`: If not zero, determines the length of the incomplete orthogonalization procedure (IOP).       Note that if the linear operator/Jacobian is hermitian, then the Lanczos algorithm will always be used and the IOP setting is ignored.

## References

@article{crouch1993numerical,   title={Numerical integration of ordinary differential equations on manifolds},   author={Crouch, Peter E and Grossman, R},   journal={Journal of Nonlinear Science},   volume={3},   pages={1–33},   year={1993},   publisher={Springer} }
