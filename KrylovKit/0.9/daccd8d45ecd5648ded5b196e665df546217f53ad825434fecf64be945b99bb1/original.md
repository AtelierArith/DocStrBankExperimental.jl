```
svdsolve(A::AbstractMatrix, [x₀, howmany = 1, which = :LR, T = eltype(A)]; kwargs...)
svdsolve(f, m::Int, [howmany = 1, which = :LR, T = Float64]; kwargs...)
svdsolve(f, x₀, [howmany = 1, which = :LR]; kwargs...)
# expert version:
svdsolve(f, x₀, howmany, which, algorithm; alg_rrule=...)
```

Compute `howmany` singular values from the linear map encoded in the matrix `A` or by the function `f`. Return singular values, left and right singular vectors and a `ConvergenceInfo` structure.

### Arguments:

The linear map can be an `AbstractMatrix` (dense or sparse) or a general function or callable object. Since both the action of the linear map and its adjoint are required in order to compute singular values, `f` can either be a tuple of two callable objects (each accepting a single argument), representing the linear map and its adjoint respectively, or, `f` can be a single callable object that accepts two input arguments, where the second argument is a flag of type `Val{true}` or `Val{false}` that indicates whether the adjoint or the normal action of the linear map needs to be computed. The latter form still combines well with the `do` block syntax of Julia, as in

```julia
vals, lvecs, rvecs, info = svdsolve(x₀, howmany, which; kwargs...) do x, flag
    if flag === Val(true)
        # y = compute action of adjoint map on x
    else
        # y = compute action of linear map on x
    end
    return y
end
```

For a general linear map encoded using either the tuple or the two-argument form, the best approach is to provide a start vector `x₀` (in the codomain, i.e. column space, of the linear map). Alternatively, one can specify the number `m` of rows of the linear map, in which case `x₀ = rand(T, m)` is used, where the default value of `T` is `Float64`, unless specified differently. If an `AbstractMatrix` is used, a starting vector `x₀` does not need to be provided; it is chosen as `rand(T, size(A, 1))`.

The next arguments are optional, but should typically be specified. `howmany` specifies how many singular values and vectors should be computed; `which` specifies which singular values should be targeted. Valid specifications of `which` are

  * `LR`: largest singular values
  * `SR`: smallest singular values However, the largest singular values tend to converge more rapidly.

### Return values:

The return value is always of the form `vals, lvecs, rvecs, info = svdsolve(...)` with

  * `vals`: a `Vector{<:Real}` containing the singular values, of length at least `howmany`, but could be longer if more singular values were converged at the same cost.
  * `lvecs`: a `Vector` of corresponding left singular vectors, of the same length as `vals`.
  * `rvecs`: a `Vector` of corresponding right singular vectors, of the same length as `vals`. Note that singular vectors are not returned as a matrix, as the linear map could act on any custom Julia type with vector like behavior, i.e. the elements of the

lists `lvecs`(`rvecs`) are objects that are typically similar to the starting guess `x₀`(`A' * x₀`), up to a possibly different `eltype`. When the linear map is a simple     `AbstractMatrix`, `lvecs` and `rvecs` will be `Vector{Vector{<:Number}}`.

  * `info`: an object of type [`ConvergenceInfo`], which has the following fields

      * `info.converged::Int`: indicates how many singular values and vectors were actually converged to the specified tolerance `tol` (see below under keyword arguments)
      * `info.residual::Vector`: a list of the same length as `vals` containing the residuals `info.residual[i] = A * rvecs[i] - vals[i] * lvecs[i]`.
      * `info.normres::Vector{<:Real}`: list of the same length as `vals` containing the norm of the residual `info.normres[i] = norm(info.residual[i])`
      * `info.numops::Int`: number of times the linear map was applied, i.e. number of times `f` was called, or a vector was multiplied with `A` or `A'`.
      * `info.numiter::Int`: number of times the Krylov subspace was restarted (see below)

!!! warning "Check for convergence"
    No warning is printed if not all requested singular values were converged, so always check if `info.converged >= howmany`.


### Keyword arguments:

Keyword arguments and their default values are given by:

  * `verbosity::Int = 0`: verbosity level

      * 0 (suppress all messages)
      * 1 (only warnings)
      * 2 (one message with convergence info at the end)
      * 3 (progress info after every iteration)
      * 4+ (all of the above and additional information about the GKL iteration)
  * `krylovdim`: the maximum dimension of the Krylov subspace that will be constructed. Note that the dimension of the vector space is not known or checked, e.g. `x₀` should not necessarily support the `Base.length` function. If you know the actual problem dimension is smaller than the default value, it is useful to reduce the value of `krylovdim`, though in principle this should be detected.
  * `tol`: the requested accuracy according to `normres` as defined above. If you work in e.g. single precision (`Float32`), you should definitely change the default value.
  * `maxiter`: the number of times the Krylov subspace can be rebuilt; see below for further details on the algorithms.
  * `orth`: the orthogonalization method to be used, see [`Orthogonalizer`](@ref)
  * `eager::Bool = false`: if true, eagerly compute the SVD after every expansion of the Krylov subspace to test for convergence, otherwise wait until the Krylov subspace has dimension `krylovdim`

The final keyword argument `alg_rrule` is relevant only when `svdsolve` is used in a setting where reverse-mode automatic differentation will be used. A custom `ChainRulesCore.rrule` is defined for `svdsolve`, which can be evaluated using different algorithms that can be specified via `alg_rrule`. A suitable default is chosen, so this keyword argument should only be used when this default choice is failing or not performing efficiently. Check the documentation for more information on the possible values for `alg_rrule` and their implications on the algorithm being used.

### Algorithm

The last method, without default values and keyword arguments, is the one that is finally called, and can also be used directly. Here the algorithm is specified, though currently only [`GKL`](@ref) is available. `GKL` refers to the the partial Golub-Kahan-Lanczos bidiagonalization which forms the basis for computing the approximation to the singular values. This factorization is dynamically shrunk and expanded (i.e. thick restart) similar to the Krylov-Schur factorization for eigenvalues.
