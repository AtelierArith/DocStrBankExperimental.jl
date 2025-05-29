```julia
LinearExponential(; krylov = :off,
                    m = 10,
                    iop = 0)
```

Semilinear ODE solver Exact solution formula for linear, time-independent problems.

### Keyword Arguments

  * `krylov`:

      * `:off`: cache the operator beforehand. Requires Matrix(A) method defined for the operator A.
      * `:simple`: uses simple Krylov approximations with fixed subspace size m.
      * `:adaptive`: uses adaptive Krylov approximations with internal timestepping.
  * `m`: Controls the size of Krylov subspace if `krylov=:simple`, and the initial subspace size if `krylov=:adaptive`.
  * `iop`: If not zero, determines the length of the incomplete orthogonalization procedure       Note that if the linear operator/Jacobian is hermitian,       then the Lanczos algorithm will always be used and the IOP setting is ignored.

## References

@book{strogatz2018nonlinear,     title={Nonlinear dynamics and chaos: with applications to physics, biology, chemistry, and engineering},     author={Strogatz, Steven H},     year={2018},     publisher={CRC press}}
