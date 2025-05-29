```
 pschur!(A::Array{Float64,3}, Z::AbstractArray{Float64,3}, ilh::Tuple(Int,Int) = (1, size(A,1)); rev = true, sind = 1, withZ = true) -> (ev, sind, α, γ)
 pschur!(wspace::Tuple, A::Array{Float64,3}, Z::AbstractArray{Float64,3}, ilh::Tuple(Int,Int) = (1, size(A,1)); rev = true, sind = 1, withZ = true) -> (ev, sind, α, γ)
```

Compute the Schur decomposition of a product of square matrices  `A(p)*...*A(2)*A(1)`, if `rev = true` (default) or `A(1)*A(2)*...*A(p)` if `rev = false`, without evaluating the product.  The matrices `A(1)`, `...`, `A(p)` are contained in the `n×n×p` array `A`  such that the `i`-th matrix `A(i)` is contained in `A[:,:,i]`.  A range `ilh = (ilo, ihi)` can be specified, such that all matrices `A(j), j = 1, ..., p`, are already in periodic Schur forms in rows and columns `1:ilo-1` and `ihi+1:n`, where `n` is the first dimension of `A`. The resulting reduced matrices `S(1)`, `...`, `S(p)`, representing the periodic Schur decimposition  overwrite the input matrices `A(1)`, `...`, `A(p)`. If `withZ = true`, then `Z` must contain on input an `n×n×p` array, which will be overwritten on output with the orthogonal matrices `Z(1)`, `...`, `Z(p)` used for reduction.  If `withZ = false`, orthogonal transformations are not computed and `Z` can be an arbiitrary three-dimensional array (e.g., an empty `0×0×0` array).  The resulting reduced matrices `S(1)`, `...`, `S(p)` and the orthogonal transformation matrices `Z(1)`, `...`, `Z(p)`,  satisfy for `rev = true`

```
       Z(2)' * A(1) * Z(1) = S(1),
       Z(3)' * A(2) * Z(2) = S(2),
              ...
       Z(1)' * A(p) * Z(p) = S(p),
```

and for `rev = false`

```
       Z(1)' * A(1) * Z(2) = S(1),
       Z(2)' * A(2) * Z(3) = S(2),
              ...
       Z(p)' * A(p) * Z(1) = S(p).
```

If `sind = ischur`, with `1 ≤ ischur ≤ p` (default `ischur = 1`), then  `S(i)`, for `i = 1, ..., p` are in a periodic Schur form,  with `S(ischur)` in quasi-upper triangular (or Schur) form and `S(i)`  upper triangular for `i` $\neq$ `ischur`.  The vector `ev` contains the eigenvalues of the appropriate matrix product.  The eigenvalues can be alternatively expressed as `α .* γ`, where `γ` contains suitable  scaling parameters to avoid overflows or underflows in the expressions of the eigenvalues. 

To reduce the number of allocations when the periodic Schur decomposition needs to be repeteadly computed,  the internally needed workspace can be pre-allocated in a tuple `wspace` using the function [`PeriodicMatrices.ws_pschur`](@ref)). 
