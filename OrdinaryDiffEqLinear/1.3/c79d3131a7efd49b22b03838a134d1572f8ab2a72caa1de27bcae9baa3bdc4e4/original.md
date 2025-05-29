```julia
RKMK2(; krylov = false,
        m = 30,
        iop = 0)
```

Semilinear ODE solver Second order Runge–Kutta–Munthe-Kaas method.

### Keyword Arguments

  * `krylov`: Determines whether Krylov approximation or operator caching is used, the latter only available for semilinear problems.   `krylov=true` is much faster for larger systems and is thus recommended whenever there are >100 ODEs.
  * `m`: Controls the size of Krylov subspace.
  * `iop`: If not zero, determines the length of the incomplete orthogonalization procedure (IOP).       Note that if the linear operator/Jacobian is hermitian, then the Lanczos algorithm will always be used and the IOP setting is ignored.

## References

@article{celledoni2014introduction,   title={An introduction to Lie group integrators–basics, new developments and applications},   author={Celledoni, Elena and Marthinsen, H{a}kon and Owren, Brynjulf},   journal={Journal of Computational Physics},   volume={257},   pages={1040–1061},   year={2014},   publisher={Elsevier} }
