The Locally Optimal Block Preconditioned Conjugate Gradient Method (LOBPCG)

Finds the `nev` extremal eigenvalues and their corresponding eigenvectors satisfying `AX = λBX`.

`A` and `B` may be generic types but `Base.mul!(C, AorB, X)` must be defined for vectors and strided matrices `X` and `C`. `size(A, i::Int)` and `eltype(A)` must also be defined for `A`.

```
lobpcg(A, [B,] largest, nev; kwargs...) -> results
```

# Arguments

  * `A`: linear operator;
  * `B`: linear operator;
  * `largest`: `true` if largest eigenvalues are desired and false if smallest;
  * `nev`: number of eigenvalues desired.

## Keywords

  * `log::Bool`: default is `false`; if `true`, `results.trace` will store iterations   states; if `false` only `results.trace` will be empty;
  * `P`: preconditioner of residual vectors, must overload `ldiv!`;
  * `C`: constraint to deflate the residual and solution vectors orthogonal   to a subspace; must overload `mul!`;
  * `maxiter`: maximum number of iterations; default is 200;
  * `tol::Real`: tolerance to which residual vector norms must be under.

# Output

  * `results`: a `LOBPCGResults` struct. `r.λ` and `r.X` store the eigenvalues and eigenvectors.
