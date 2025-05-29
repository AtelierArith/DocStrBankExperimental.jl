lobpcg(A, [B,] largest, X0, nev; kwargs...) -> results

# Arguments

  * `A`: linear operator;
  * `B`: linear operator;
  * `largest`: `true` if largest eigenvalues are desired and false if smallest;
  * `X0`: block vectors such that the eigenvalues will be found size(X0, 2) at a time;   the columns are also used to initialize the first batch of Ritz vectors;
  * `nev`: number of eigenvalues desired.

## Keywords

  * `log::Bool`: default is `false`; if `true`, `results.trace` will store iterations   states; if `false` only `results.trace` will be empty;
  * `P`: preconditioner of residual vectors, must overload `ldiv!`;
  * `C`: constraint to deflate the residual and solution vectors orthogonal   to a subspace; must overload `mul!`;
  * `maxiter`: maximum number of iterations; default is 200;
  * `tol::Real`: tolerance to which residual vector norms must be under.

# Output

  * `results`: a `LOBPCGResults` struct. `r.λ` and `r.X` store the eigenvalues and eigenvectors.
