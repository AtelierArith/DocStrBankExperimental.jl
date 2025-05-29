```julia
MagnusGL6(; krylov = false,
            m = 30,
            iop = 0)
```

Semilinear ODE solver Sixth order Magnus method approximated using Gauss-Legendre quadrature.

### Keyword Arguments

  * `krylov`: Determines whether Krylov approximation or operator caching is used, the latter only available for semilinear problems.   `krylov=true` is much faster for larger systems and is thus recommended whenever there are >100 ODEs.
  * `m`: Controls the size of Krylov subspace.
  * `iop`: If not zero, determines the length of the incomplete orthogonalization procedure (IOP).       Note that if the linear operator/Jacobian is hermitian, then the Lanczos algorithm will always be used and the IOP setting is ignored.

## References

@article{blanes2000improved,   title={Improved high order integrators based on the Magnus expansion},   author={Blanes, Sergio and Casas, Fernando and Ros, Javier},   journal={BIT Numerical Mathematics},   volume={40},   number={3},   pages={434–450},   year={2000},   publisher={Springer} }
