```
tsvd(A, nvals = 1; [maxiter, initvec, tolconv, tolreorth, debug])
```

Computes the truncated singular value decomposition (TSVD) by Lanczos bidiagonalization of the operator `A`. The Lanczos vectors are partially orthogonalized as described in

R. M. Larsen, *Lanczos bidiagonalization with partial reorthogonalization*, Department of Computer Science, Aarhus University, Technical report, DAIMI PB-357, September 1998.

# Positional arguments:

  * `A`: Anything that supports the in place update operations

```
mul!(y::AbstractVector, A, x::AbstractVector, α::Number, β::Number)
```

and

```
mul!(y::AbstractVector, A::Adjoint, x::AbstractVector, α::Number, β::Number)
```

corresponding to the operations `y := α*op(A)*x + β*y` where `op` can be either the identity or the conjugate transpose of `A`. If the `initvec` argument is not supplied then it is furthermore required that `A` supports `eltype` and `size`.

  * `nvals`: The number of singular values and vectors to compute. Default is one (the largest).

# Keyword arguments:

  * `maxiter`: The maximum number of iterations of the Lanczos bidiagonalization. Default is 1000, but usually much fewer iterations are needed.
  * `initvec`: Initial `U` vector for the Lanczos procesdure. Default is a vector of Gaussian random variates. The `length` and `eltype` of the `initvec` will control the size and element types of the basis vectors in `U` and `V`.
  * `tolconv`: Relative convergence criterion for the singular values. Default is `sqrt(eps(real(eltype(A))))`.
  * `tolreorth`: Absolute tolerance for the inner product of the Lanczos vectors as measured by the ω recurrence. Default is `sqrt(eps(real(eltype(initvec))))`. `0.0` and `Inf` correspond to complete and no reorthogonalization respectively.
  * `debug`: Boolean flag for printing debug information

# Output:

The output of the procesure it the truple tuple `(U, s, V)`

  * `U`: `size(A, 1)` times `nvals` matrix of left singular vectors.
  * `s`: Vector of length `nvals` of the singular values of `A`.
  * `V`: `size(A, 2)` times `nvals` matrix of right singular vectors.

# Examples

```jldoctest
julia> A = matrixdepot("LPnetlib/lp_osa_30")
4350×104374 SparseArrays.SparseMatrixCSC{Float64, Int64} with 604488 stored entries:
⠙⠮⠷⠶⠽⠶⠽⠶⠮⠷⠮⠷⠶⠽⠶⠽⠶⠬⠷⠮⠷⠦⠽⠶⠽⠶⠽⠶⠮⠷⠮⠷⠶⠽⠶⠽⠶⠭⠷⠦

julia> U, s, V = tsvd(A, 5);

julia> round.(s, digits=7)
5-element Vector{Float64}:
 1365.8944098
 1033.2125634
  601.3524529
  554.107656
  506.0414587
```
