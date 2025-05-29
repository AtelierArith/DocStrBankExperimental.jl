```
svdl(A) -> Σ, L, [history]
```

Compute some singular values (and optionally vectors) using Golub-Kahan-Lanczos bidiagonalization [^Golub1965] with thick restarting [^Wu2000].

If `log` is set to `true` is given, method will output a tuple `X, L, ch`. Where `ch` is a `ConvergenceHistory` object. Otherwise it will only return `X, L`.

# Arguments

  * `A` : The matrix or matrix-like object whose singular values are desired.

## Keywords

  * `nsv::Int = 6`: number of singular values requested;
  * `v0 = random unit vector`: starting guess vector in the domain of `A`. The length of `q` should be the number of columns in `A`;
  * `k::Int = 2nsv`: maximum number of Lanczos vectors to compute before restarting;
  * `j::Int = nsv`: number of vectors to keep at the end of the restart. We don't recommend j < nsv;
  * `maxiter::Int = minimum(size(A))`: maximum number of iterations to run;
  * `verbose::Bool = false`: print information at each iteration;
  * `tol::Real = √eps()`: maximum absolute error in each desired singular value;
  * `reltol::Real=√eps()`: maximum error in each desired singular value relative to the estimated norm of the input matrix;
  * `method::Symbol=:ritz`: restarting algorithm to use. Valid choices are:

    1. `:ritz`: Thick restart with Ritz values [Wu2000].
    2. `:harmonic`: Restart with harmonic Ritz values [Baglama2005].
  * `vecs::Symbol = :none`: singular vectors to return.

    1. `:both`: Both left and right singular vectors are returned.
    2. `:left`: Only the left singular vectors are returned.
    3. `:right`: Only the right singular vectors are returned.
    4. `:none`: No singular vectors are returned.
  * `dolock::Bool=false`: If `true`, locks converged Ritz values, removing them from the Krylov subspace being searched in the next macroiteration;
  * `log::Bool = false`: output an extra element of type `ConvergenceHistory` containing extra information of the method execution.

# Return values

**if `log` is `false`**

  * `Σ`: list of the desired singular values if `vecs == :none` (the default), otherwise returns an `SVD` object with the desired singular vectors filled in;
  * `L`: computed partial factorizations of A.

**if `log` is `true`**

  * `Σ`: list of the desired singular values if `vecs == :none` (the default),

otherwise returns an `SVD` object with the desired singular vectors filled in;

  * `L`: computed partial factorizations of A;
  * `history`: convergence history.

**ConvergenceHistory keys**

  * `:betas` => `betas`: The history of the computed betas.
  * `:Bs` => `Bs`: The history of the computed projected matrices.
  * `:ritz` => `ritzvalhist`: Ritz values computed at each iteration.
  * `:conv` => `convhist`: Convergence data.

[^Golub1965]: Golub, Gene, and William Kahan. "Calculating the singular values and pseudo-inverse of a matrix." Journal of the Society for Industrial and Applied Mathematics, Series B: Numerical Analysis 2.2 (1965): 205-224.

[^Wu2000]: Wu, Kesheng, and Horst Simon. "Thick-restart Lanczos method for large symmetric eigenvalue problems." SIAM Journal on Matrix Analysis and Applications 22.2 (2000): 602-616.
