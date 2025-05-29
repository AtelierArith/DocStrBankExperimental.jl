```
# expert version:
schursolve(f, x₀, howmany, which, algorithm)
```

Compute a partial Schur decomposition containing `howmany` eigenvalues from the linear map encoded in the matrix or function `A`. Return the reduced Schur matrix, the basis of Schur vectors, the extracted eigenvalues and a `ConvergenceInfo` structure.

See also [`eigsolve`](@ref) to obtain the eigenvectors instead. For real symmetric or complex hermitian problems, the (partial) Schur decomposition is identical to the (partial) eigenvalue decomposition, and `eigsolve` should always be used.

### Arguments:

The linear map can be an `AbstractMatrix` (dense or sparse) or a general function or callable object, that acts on vector like objects similar to `x₀`, which is the starting guess from which a Krylov subspace will be built. `howmany` specifies how many Schur vectors should be converged before the algorithm terminates; `which` specifies which eigenvalues should be targeted. Valid specifications of `which` are

  * `LM`: eigenvalues of largest magnitude
  * `LR`: eigenvalues with largest (most positive) real part
  * `SR`: eigenvalues with smallest (most negative) real part
  * `LI`: eigenvalues with largest (most positive) imaginary part, only if `T <: Complex`
  * `SI`: eigenvalues with smallest (most negative) imaginary part, only if `T <: Complex`
  * [`EigSorter(f; rev = false)`](@ref): eigenvalues `λ` that appear first (or last if `rev == true`) when sorted by `f(λ)`

!!! note "Note about selecting `which` eigenvalues"
    Krylov methods work well for extremal eigenvalues, i.e. eigenvalues on the periphery of the spectrum of the linear map. All of they valid `Symbol`s for `which` have this property, but could also be specified using `EigSorter`, e.g. `:LM` is equivalent to `Eigsorter(abs; rev = true)`. Note that smallest magnitude sorting is obtained using e.g. `EigSorter(abs; rev = false)`, but since no (shift-and)-invert is used, this will only be successful if you somehow know that eigenvalues close to zero are also close to the periphery of the spectrum.


!!! warning "Degenerate eigenvalues"
    From a theoretical point of view, Krylov methods can at most find a single eigenvector associated with a targetted eigenvalue, even if the latter is degenerate. In the case of a degenerate eigenvalue, the specific eigenvector that is returned is determined by the starting vector `x₀`. For large problems, this turns out to be less of an issue in practice, as often a second linearly independent eigenvector is generated out of the numerical noise resulting from the orthogonalisation steps in the Lanczos or Arnoldi iteration. Nonetheless, it is important to take this into account and to try not to depend on this potentially fragile behaviour, especially for smaller problems.


The `algorithm` argument currently only supports an instance of [`Arnoldi`](@ref), which is where the parameters of the Krylov method (such as Krylov dimension and maximum number of iterations) can be specified. Since `schursolve` is less commonly used as `eigsolve`, it only supports this expert mode call syntax and no convenient keyword interface is currently available.

### Return values:

The return value is always of the form `T, vecs, vals, info = schursolve(...)` with

  * `T`: a `Matrix` containing the partial Schur decomposition of the linear map, i.e. it's elements are given by `T[i,j] = inner(vecs[i], f(vecs[j]))`. It is of Schur form, i.e. upper triangular in case of complex arithmetic, and block upper triangular (with at most 2x2 blocks) in case of real arithmetic.
  * `vecs`: a `Vector` of corresponding Schur vectors, of the same length as `vals`. Note that Schur vectors are not returned as a matrix, as the linear map could act on any custom  Julia type with vector like behavior, i.e. the elements of the list `vecs` are objects that are typically similar to the starting guess `x₀`, up to a possibly different `eltype`. When the linear map is a simple `AbstractMatrix`, `vecs` will be `Vector{Vector{<:Number}}`. Schur vectors are by definition orthogonal, i.e. `inner(vecs[i],vecs[j]) = I[i,j]`. Note that Schur vectors are real if the problem (i.e. the linear map and the initial guess) are real.
  * `vals`: a `Vector` of eigenvalues, i.e. the diagonal elements of `T` in case of complex arithmetic, or extracted from the diagonal blocks in case of real arithmetic. Note that `vals` will always be complex, independent of the underlying arithmetic.
  * `info`: an object of type [`ConvergenceInfo`], which has the following fields

      * `info.converged::Int`: indicates how many eigenvalues and Schur vectors were actually converged to the specified tolerance (see below under keyword arguments)
      * `info.residuals::Vector`: a list of the same length as `vals` containing the actual residuals

        ```julia
        info.residuals[i] = f(vecs[i]) - sum(vecs[j] * T[j, i] for j in 1:i+1)
        ```

        where `T[i+1,i]` is definitely zero in case of complex arithmetic and possibly zero in case of real arithmetic
      * `info.normres::Vector{<:Real}`: list of the same length as `vals` containing the norm of the residual for every Schur vector, i.e. `info.normes[i] = norm(info.residual[i])`
      * `info.numops::Int`: number of times the linear map was applied, i.e. number of times `f` was called, or a vector was multiplied with `A`
      * `info.numiter::Int`: number of times the Krylov subspace was restarted (see below)

!!! warning "Check for convergence"
    No warning is printed if not all requested eigenvalues were converged, so always check if `info.converged >= howmany`.


### Algorithm

The actual algorithm is an implementation of the Krylov-Schur algorithm, where the [`Arnoldi`](@ref) algorithm is used to generate the Krylov subspace. During the algorithm, the Krylov subspace is dynamically grown and shrunk, i.e. the restarts are so-called thick restarts where a part of the current Krylov subspace is kept.
