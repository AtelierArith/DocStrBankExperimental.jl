```
nleigs(nep::NEP, Σ::AbstractVector{Complex{T}})
```

Find a few eigenvalues and eigenvectors of a nonlinear eigenvalue problem, using the `nleigs` algorithm.

# Arguments

  * `nep`: An instance of a nonlinear eigenvalue problem.
  * `Σ`: A vector containing the points of a polygonal target set in the complex plane.
  * `Ξ`: A vector containing a discretization of the singularity set.
  * `logger`: Level of display (0, 1, 2).
  * `maxdgr`: Max degree of approximation.
  * `minit`: Min number of iterations after linearization is converged.
  * `maxit`: Max number of total iterations.
  * `tol`: Tolerance for residual.
  * `tollin`: Tolerance for convergence of linearization.
  * `v`: Starting vector.
  * `errmeasure`: Function for error measure (residual norm). Called with arguments (λ,v).
  * `isfunm` : Whether to use matrix functions.
  * `static`: Whether to use static version of NLEIGS.
  * `leja`: Use of Leja-Bagby points (0 = no, 1 = only in expansion phase, 2 = always).
  * `nodes`: Prefixed interpolation nodes (only when leja is 0 or 1).
  * `reusefact`: Reuse of matrix factorizations (0 = no, 1 = only after converged linearization, 2 = always).
  * `blksize`: Block size for pre-allocation.
  * `return_details`: Whether to return solution details (see NleigsSolutionDetails).
  * `check_error_every`: Check for convergence / termination every this number of iterations.

See [`augnewton`](@ref) for other parameters.

# Return values

  * `λ`: Vector of eigenvalues of the nonlinear eigenvalue problem NLEP inside the target set Σ.
  * `X`: Corresponding matrix of eigenvectors.
  * `res`: Corresponding residuals.
  * `details`: Solution details, if requested (see NleigsSolutionDetails).

# Example

```julia-repl
julia> nep=nep_gallery("dep0");
julia> unit_square = float([1+1im, 1-1im, -1-1im,-1+1im])
julia> (λ,v)=nleigs(nep,unit_square);
julia> norm(compute_Mlincomb(nep,λ[1],v[:,1]))
5.028313023882492e-14
julia> norm(compute_Mlincomb(nep,λ[2],v[:,2]))
1.1937025845487509e-13
```

# References

  * S. Guettel, R. Van Beeumen, K. Meerbergen, and W. Michiels. NLEIGS: A class of fully rational Krylov methods for nonlinear eigenvalue problems. SIAM J. Sci. Comput., 36(6), A2842-A2864, 2014.
  * [NLEIGS Matlab toolbox](http://twr.cs.kuleuven.be/research/software/nleps/nleigs.php) (GPL License)
  * [NLEIGS Matlab toolbox](https://bitbucket.org/roelvb/nleigs) (MIT License)
