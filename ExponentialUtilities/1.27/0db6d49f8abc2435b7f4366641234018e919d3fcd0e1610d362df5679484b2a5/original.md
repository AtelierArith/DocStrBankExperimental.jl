```
kiops(tstops, A, u; kwargs...) -> (w, stats)
```

Evaluate a linear combination of the $φ$ functions evaluated at $tA$ acting on vectors from $u$, that is

$$
  w(i) = φ_0(t[i] A) u[:, 1] + φ_1(t[i] A) u[:, 2] + φ_2(t[i] A) u[:, 3] + ...
$$

The size of the Krylov subspace is changed dynamically during the integration. The Krylov subspace is computed using the incomplete orthogonalization method.

Arguments:

  * `tstops`     - Array of `tstop`
  * `A`          - the matrix argument of the $φ$ functions
  * `u`          - the matrix with columns representing the vectors to be multiplied by the $φ$ functions

Keyword arguments:

  * `tol`        - the convergence tolerance required (default: 1e-7)
  * `mmin`, `mmax` - let the Krylov size vary between mmin and mmax (default: 10, 128)
  * `m`          - an estimate of the appropriate Krylov size (default: mmin)
  * `iop`        - length of incomplete orthogonalization procedure (default: 2)
  * `ishermitian` -  whether $A$ is Hermitian (default: ishermitian(A))
  * `opnorm`     -  the operator norm of $A$ (default: opnorm(A, Inf))
  * `task1`      - if true, divide the result by 1/T^p

Returns:

  * `w`        - the linear combination of the $φ$ functions evaluated at $tA$ acting on the vectors from $u$
  * `stats[1]` - number of substeps
  * `stats[2]` - number of rejected steps
  * `stats[3]` - number of Krylov steps
  * `stats[4]` - number of matrix exponentials
  * `stats[5]` - the Krylov size of the last substep

`n` is the size of the original problem `p` is the highest index of the $φ$ functions

References:

  * Gaudreault, S., Rainwater, G. and Tokman, M., 2018. KIOPS: A fast adaptive Krylov subspace solver for exponential integrators. Journal of Computational Physics. Based on the PHIPM and EXPMVP codes (http://www1.maths.leeds.ac.uk/~jitse/software.html). https://gitlab.com/stephane.gaudreault/kiops.
  * Niesen, J. and Wright, W.M., 2011. A Krylov subspace method for option pricing. SSRN 1799124
  * Niesen, J. and Wright, W.M., 2012. Algorithm 919: A Krylov subspace algorithm for evaluating the $φ$-functions appearing in exponential integrators. ACM Transactions on Mathematical Software (TOMS), 38(3), p.22
