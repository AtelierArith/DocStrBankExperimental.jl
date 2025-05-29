```
S,V = broyden([eltype,]nep::NEP[,approxnep];kwargs)
```

Runs Broydens method (with deflation) for the nonlinear eigenvalue problem defined by nep. An approximate nep can be provided which is used as an initialization of starting matrix/vectors. The optional argument `approxnep` determines how  to initiate the algorithm. It can be an `NEP`, the symbol `:eye` corresponding to starting with an identity matrix, and a `Matrix` (of size $n	imes n$). Beside most of the standard kwargs as described in [`augnewton`](@ref), it supports `pmax` which is subspace used in deflation, essentially the number of eigenvalues, `add_nans::Bool`  which determines if `NaNs` should be added in book keeping. `eigmethod` which can be `:eig`, `:eigs` or `:invpow`. The `:invpow` is an implementation of the power method, which is slow but works well e.g. for `BigFloat`. The kwarg `recompute_U` determines if the `U`-matrix should be recomputed in every deflation (which can be more robust). The implementation has two loggers `logger` and `inner_logger`. The `logger` corresponds to outer iterations (deflation) and  `inner_logger` is the iterates in Broydens method. The kwarg `check_error_every` and `print_error_every`   detemine how often errors should be check and how often they should be printed. For real problems with complex conjugate symmetry, you may want to set the kwarg `addconj=true` in order to reduce computation by automatically adding the complex conjugate vectors.

The method computes an invariant pair and can therefore find several eigenvalues. The retured value is (S,V) is an invariant pair and the eigenvalues are on the diagonal of S. Eigenpairs can be directly extracted with [`get_deflated_eigpairs`](@ref).

# Example

```julia-repl
julia> nep=nep_gallery("dep0");
julia> S,V=broyden(nep);
julia> λ=S[1,1]
-0.15955391823299253 - 3.874865266487398e-19im
julia> minimum(svdvals(compute_Mder(nep,λ)))
1.6293996560844023e-16
julia> λ=S[2,2]
-0.5032087003825461 + 1.1969823800738464im
julia> minimum(svdvals(compute_Mder(nep,λ)))
1.1073470346550144e-15
julia> λ=S[3,3]
1.2699713558173726 + 5.342786996459857e-16im
julia> minimum(svdvals(compute_Mder(nep,λ)))
5.905315846211231e-16
julia> broyden(nep,logger=2,check_error_every=1);  # Prints out a lot more convergence info
```

In order to extract eigenpairs you can use the following:

```julia-repl
julia> (D,X)=get_deflated_eigpairs(S,V,size(nep,1));
julia> for i=1:3; @show norm(compute_Mlincomb(nep,D[i],X[:,i])); end
norm(compute_Mlincomb(nep, D[i], X[:, i])) = 8.459878994614521e-13
norm(compute_Mlincomb(nep, D[i], X[:, i])) = 1.2102336671048442e-13
norm(compute_Mlincomb(nep, D[i], X[:, i])) = 2.1012363973403225e-16
```

# References

  * Jarlebring, Broyden’s method for nonlinear eigenproblems, SIAM J. Sci. Comput., 41:A989–A1012, 2019, https://arxiv.org/pdf/1802.07322
