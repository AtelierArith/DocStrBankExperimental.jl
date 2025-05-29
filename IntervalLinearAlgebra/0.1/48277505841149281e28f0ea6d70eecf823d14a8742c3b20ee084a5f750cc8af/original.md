```
verify_eigen(A[, λ, X0]; w=0.1, ϵ=1e-16, maxiter=10)
```

Finds a rigorous bound for the eigenvalues and eigenvectors of `A`. Eigenvalues are treated as simple.

### Input

  * `A`       – matrix
  * `λ`       – (optional) approximate value for an eigenvalue of `A`
  * `X0`      – (optional) eigenvector associated to `λ`
  * `w`       – relative inflation parameter
  * `ϵ`       – absolute inflation parameter
  * `maxiter` – maximum number of iterations

### Output

  * Interval bounds on eigenvalues and eigenvectors.
  * A boolean certificate (or a vector of booleans if all eigenvalues are computed) `cert`. If `cert[i]==true`, then the bounds for the ith eigenvalue and eigenvectore are rigorous, otherwise not.

### Algorithm

The algorithm for this function is described in [[RUM01]](@ref).

### Example

```julia
julia> A = Symmetric([1 2;2 3])
2×2 Symmetric{Int64, Matrix{Int64}}:
 1  2
 2  3

julia> evals, evecs, cert = verify_eigen(A);

julia> evals
2-element Vector{Interval{Float64}}:
 [-0.236068, -0.236067]
  [4.23606, 4.23607]

julia> evecs
2×2 Matrix{Interval{Float64}}:
 [-0.850651, -0.85065]  [0.525731, 0.525732]
  [0.525731, 0.525732]  [0.85065, 0.850651]

julia> cert
2-element Vector{Bool}:
 1
 1
```
