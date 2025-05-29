```
equilibrate!(A::AbstractMatrix{T},
             D1::Diagonal{T, S}, D2::Diagonal{T, S},
             R_k::Diagonal{T, S}, C_k::Diagonal{T, S};
             ϵ::T = T(1.0e-2), max_iter::Int = 100,
             A_transposed::Bool = false) where {T, S <: AbstractVector{T}}
```

Performs the equilibration algorithm to scale `A` so that its rows and columns have a infinity norm of 1 with a tolerance `ϵ`. `D1` and `D2` are diagonal scaling factors of sizes `size(A, 1)` and `size(A, 2)` respectively. Once `A` is scaled, the identity `inv(D1) * A * inv(D2)` gives the unscaled matrix. `R_k` and `C_k` are diagonal matrices of sizes `size(A, 1)` and `size(A, 2)` respectively that should be pre-allocated. `max_iter` is the maximal number of iterations.

If `A_transposed = true`, then, once `A` is scaled, the identity `inv(D2) * A * inv(D1)` gives the unscaled matrix. When using `A_transposed = true`, `D1` and `D2` should have sizes `size(A, 2)` and `size(A, 1)`.

```
equilibrate!(Q::Symmetric{T}, D::Diagonal{T, S}, C_k::Diagonal{T, S};
             ϵ::T = T(1.0e-2), max_iter::Int = 100) where {T, S <: AbstractVector{T}}
```

Performs the equilibration algorithm to scale the symmetric matrix `Q` so that its rows and columns have a infinity norm of 1 with a tolerance `ϵ`. `D` is a diagonal scaling factors of size `size(Q, 1)`. Once `Q` is scaled, the identity `inv(D) * Q * inv(D)` gives the unscaled matrix. `C_k` is a diagonal matrix of size `size(A, 1)` that should be pre-allocated. `max_iter` is the maximal number of iterations.

# Reference

  * D. Ruiz, *A Scaling Algorithm to Equilibrate Both Rows and Columns Norms in Matrices*, RAL-TR-2001-034, 2001.
