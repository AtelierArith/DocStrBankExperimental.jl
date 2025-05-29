```
λ,v = sgiter([eltype],nep::NEP,j::Integer;[λ_min,][λ_max,][λ,][errmeasure,][tol,][maxit,][logger,][eigsolvertype::Type,])
```

Finds the `j`-th eigenvalue of the NEP using safeguarded iteration, with eigenvalue numbering according to min-max theory. The method only works for Hermitian problems, and the eigenvalues are assumed to be real. If an interval [`λ_min`,`λ_max`] is given, then the Rayleigh functional is assumed to be unique on the interval. If no interval is given, then the minimum solution is always taken. The method requires the computation of (all) eigenvalues of a matrix. The `eigsolvertype` is a `Type` that specifies which eigevalue solver is used inside the algorithm.

See [`augnewton`](@ref) for other parameters.

# Example

```julia-repl
julia> nep = nep_gallery("real_quadratic");
julia> λ,v = sgiter(nep, 1, λ_min = -10, λ_max = 0,  λ = -10, maxit = 100);
julia> minimum(svdvals(compute_Mder(nep,λ)))
0.0
julia> norm(v)
1.0
```

# References

  * V. Mehrmann and H. Voss, Nonlinear eigenvalue problems: a challenge for modern eigenvalue methods, GAMM‐Mitteilungen 27.2 (2004): 121-152.
  * H. Voss and B. Werner, Solving sparse nonlinear eigenvalue problems. Technical Report 82/4, Inst. f. Angew. Mathematik, Universität Hamburg, 1982.
  * B. Werner. Das Spektrum von Operatorenscharen mit verallgemeinerten Rayleighquotienten. PhD thesis, Fachbereich Mathematik, Universität Hamburg, 1970
