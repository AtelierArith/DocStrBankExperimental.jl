```julia
CG4a(; krylov = false,
       m = 30,
       iop = 0)
```

Semilinear ODE solver  Fourth order Crouch-Grossman method.

### Keyword Arguments

  * `krylov`: Determines whether Krylov approximation or operator caching is used, the latter only available for semilinear problems.   `krylov=true` is much faster for larger systems and is thus recommended whenever there are >100 ODEs.
  * `m`: Controls the size of Krylov subspace.
  * `iop`: If not zero, determines the length of the incomplete orthogonalization procedure (IOP).       Note that if the linear operator/Jacobian is hermitian, then the Lanczos algorithm will always be used and the IOP setting is ignored.

## References

@article{jackiewicz2000construction,   title={Construction of Runge–Kutta methods of Crouch–Grossman type of high order},   author={Jackiewicz, Zdzislaw and Marthinsen, Arne and Owren, Brynjulf},   journal={Advances in Computational Mathematics},   volume={13},   pages={405–415},   year={2000},   publisher={Springer} }
