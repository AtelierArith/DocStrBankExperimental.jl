```
# expert version:
realeigsolve(f, x₀, howmany, which, algorithm; alg_rrule=algorithm)
```

Compute the first `howmany` eigenvalues (according to the order specified by `which`) from the real linear map encoded in the matrix `A` or by the function `f`, if it can be guaranteed that these eigenvalues (and thus their associated eigenvectors) are real. An error will be thrown if there are complex eigenvalues within the first `howmany` eigenvalues.

Return eigenvalues, eigenvectors and a `ConvergenceInfo` structure.

!!! note "Note about real linear maps"
    A function `f` is said to implement a real linear map if it satisfies  `f(add(x,y)) = add(f(x), f(y)` and `f(scale(x, α)) = scale(f(x), α)` for vectors `x` and `y` and scalars `α::Real`. Note that this is possible even when the vectors are represented using complex arithmetic. For example, the map `f=x-> x + conj(x)` represents a real linear map that is not (complex) linear, as it does not satisfy `f(scale(x, α)) = scale(f(x), α)` for complex scalars `α`. Note that complex linear maps are always real linear maps and thus can be used in this context, if looking specifically for real eigenvalues that they may have.

    To interpret the vectors `x` and `y` as elements from a real vector space, the standard inner product defined on them will be replaced with `real(inner(x,y))`. This has no effect if the vectors `x` and `y` were represented using real arithmetic to begin with, and allows to seemlessly use complex vectors as well.


### Arguments:

The linear map can be an `AbstractMatrix` (dense or sparse) or a general function or callable object. A starting vector `x₀` needs to be provided. Note that `x₀` does not need to be of type `AbstractVector`; any type that behaves as a vector and supports the required interface (see KrylovKit docs) is accepted.

The argument `howmany` specifies how many eigenvalues should be computed; `which` specifies which eigenvalues should be targeted. Valid specifications of `which` for real problems are given by

  * `:LM`: eigenvalues of largest magnitude
  * `:LR`: eigenvalues with largest (most positive) real part
  * `:SR`: eigenvalues with smallest (most negative) real part
  * [`EigSorter(f; rev = false)`](@ref): eigenvalues `λ` that appear first (or last if `rev == true`) when sorted by `f(λ)`

!!! note "Note about selecting `which` eigenvalues"
    Krylov methods work well for extremal eigenvalues, i.e. eigenvalues on the periphery of the spectrum of the linear map. All of the valid `Symbol`s for `which` have this property, but could also be specified using `EigSorter`, e.g. `:LM` is equivalent to `Eigsorter(abs; rev = true)`. Note that smallest magnitude sorting is obtained using e.g. `EigSorter(abs; rev = false)`, but since no (shift-and)-invert is used, this will only be successful if you somehow know that eigenvalues close to zero are also close to the periphery of the spectrum.


!!! warning "Degenerate eigenvalues"
    From a theoretical point of view, Krylov methods can at most find a single eigenvector associated with a targetted eigenvalue, even if the latter is degenerate. In the case of a degenerate eigenvalue, the specific eigenvector that is returned is determined by the starting vector `x₀`. For large problems, this turns out to be less of an issue in practice, as often a second linearly independent eigenvector is generated out of the numerical noise resulting from the orthogonalisation steps in the Lanczos or Arnoldi iteration. Nonetheless, it is important to take this into account and to try not to depend on this potentially fragile behaviour, especially for smaller problems.


The `algorithm` argument currently only supports an instance of [`Arnoldi`](@ref), which is where the parameters of the Krylov method (such as Krylov dimension and maximum number of iterations) can be specified. Since `realeigsolve` is less commonly used as `eigsolve`, it only supports this expert mode call syntax and no convenient keyword interface is currently available.

The keyword argument `alg_rrule` can be used to specify an algorithm to be used for computing the `pullback` of `realeigsolve` in the context of reverse-mode automatic differentation.

### Return values:

The return value is always of the form `vals, vecs, info = eigsolve(...)` with

  * `vals`: a `Vector` containing the eigenvalues, of length at least `howmany`, but could be longer if more eigenvalues were converged at the same cost. Eigenvalues will be real, an `ArgumentError` will be thrown if the first `howmany` eigenvalues ordered according to `which` of the linear map are not all real.
  * `vecs`: a `Vector` of corresponding eigenvectors, of the same length as `vals`. Note that eigenvectors are not returned as a matrix, as the linear map could act on any custom Julia type with vector like behavior, i.e. the elements of the list `vecs` are objects that are typically similar to the starting guess `x₀`. For a real problem with real eigenvalues, also the eigenvectors will be real and no complex arithmetic is used anywhere.
  * `info`: an object of type [`ConvergenceInfo`], which has the following fields

      * `info.converged::Int`: indicates how many eigenvalues and eigenvectors were actually converged to the specified tolerance `tol` (see below under keyword arguments)
      * `info.residual::Vector`: a list of the same length as `vals` containing the residuals `info.residual[i] = f(vecs[i]) - vals[i] * vecs[i]`
      * `info.normres::Vector{<:Real}`: list of the same length as `vals` containing the norm of the residual `info.normres[i] = norm(info.residual[i])`
      * `info.numops::Int`: number of times the linear map was applied, i.e. number of times `f` was called, or a vector was multiplied with `A`
      * `info.numiter::Int`: number of times the Krylov subspace was restarted (see below)

!!! warning "Check for convergence"
    No warning is printed if not all requested eigenvalues were converged, so always check if `info.converged >= howmany`.

