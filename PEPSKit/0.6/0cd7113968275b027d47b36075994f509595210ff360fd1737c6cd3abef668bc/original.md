```
leading_boundary(env₀, network; kwargs...) -> env, info
# expert version:
leading_boundary(env₀, network, alg::CTMRGAlgorithm)
```

Contract `network` using CTMRG and return the CTM environment. The algorithm can be supplied via the keyword arguments or directly as an [`CTMRGAlgorithm`](@ref) struct.

## Keyword arguments

### CTMRG iterations

  * `tol::Real=1.0e-8` : Stopping criterium for the CTMRG iterations. This is the norm convergence, as well as the distance in singular values of the corners and edges.
  * `miniter::Int=4` : Minimal number of CTMRG iterations.
  * `maxiter::Int=100` : Maximal number of CTMRG iterations.
  * `verbosity::Int=2` : Output verbosity level, should be one of the following:

    0. Suppress all output
    1. Only print warnings
    2. Initialization and convergence info
    3. Iteration info
    4. Debug info
  * `alg::Symbol=:simultaneous` : Variant of the CTMRG algorithm. See also [`CTMRGAlgorithm`](@ref).

      * `:simultaneous`: Simultaneous expansion and renormalization of all sides.
      * `:sequential`: Sequential application of left moves and rotations.

### Projector algorithm

  * `trscheme::Union{TruncationScheme,NamedTuple}=(; alg::Symbol=:fixedspace)` : Truncation scheme for the projector computation, which controls the resulting virtual spaces. Here, `alg` can be one of the following:

      * `:fixedspace` : Keep virtual spaces fixed during projection
      * `:notrunc` : No singular values are truncated and the performed SVDs are exact
      * `:truncerr` : Additionally supply error threshold `η`; truncate to the maximal virtual dimension of `η`
      * `:truncdim` : Additionally supply truncation dimension `η`; truncate such that the 2-norm of the truncated values is smaller than `η`
      * `:truncspace` : Additionally supply truncation space `η`; truncate according to the supplied vector space
      * `:truncbelow` : Additionally supply singular value cutoff `η`; truncate such that every retained singular value is larger than `η`
  * `svd_alg::Union{<:SVDAdjoint,NamedTuple}` : SVD algorithm for computing projectors. See also [`SVDAdjoint`](@ref). By default, a reverse-rule tolerance of `tol=1e1tol` where the `krylovdim` is adapted to the `env₀` environment dimension.
  * `projector_alg::Symbol=:halfinfinite` : Variant of the projector algorithm. See also [`ProjectorAlgorithm`](@ref).

      * `:halfinfinite` : Projection via SVDs of half-infinite (two enlarged corners) CTMRG environments.
      * `:fullinfinite` : Projection via SVDs of full-infinite (all four enlarged corners) CTMRG environments.

## Return values

The CTMRG routine returns the final CTMRG environment as well as an information `NamedTuple` containing the following fields:

  * `truncation_error` : Last (maximal) SVD truncation error of the CTMRG projectors.
  * `condition_number` : Last (maximal) condition number of the enlarged CTMRG environment.

In case the `alg` is a `SimultaneousCTMRG`, the last SVD will also be returned:

  * `U` : Last unit cell of left singular vectors.
  * `S` : Last unit cell of singular values.
  * `V` : Last unit cell of right singular vectors.

If, in addition, the specified SVD algorithm computes the full, untruncated SVD, the full set of vectors and values will be returned as well:

  * `U_full` : Last unit cell of all left singular vectors.
  * `S_full` : Last unit cell of all singular values.
  * `V_full` : Last unit cell of all right singular vectors.
