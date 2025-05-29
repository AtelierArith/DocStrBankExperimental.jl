```
implicit_eigval(A, B, eigsolve)
```

Make eigenvalue problems AD compatible with ForwardDiff and ReverseDiff

# Arguments

  * `A::matrix`, `B::matrix`: generlized eigenvalue problem. A v = λ B v  (B is identity for standard eigenvalue problem)
  * `eigsolve::function`: λ, V, U = eigsolve(A, B). Function to solve the eigenvalue problem.   λ is a vector containing eigenvalues.   V is a matrix whose columns are the corresponding eigenvectors (i.e., λ[i] corresponds to V[:, i]).   U is a matrix whose columns contain the left eigenvectors (u^H A = λ u^H B)   The left eigenvectors must be in the same order as the right ones (i.e., U' * B * V must be diagonal).   U can be provided with any normalization as we normalize internally s.t. U' * B * V = I   If A and B are symmetric/Hermitian then U = V.

# Returns

  * `λ::vector`: eigenvalues and their derivatives.  (Currently only eigenvalue derivatives are provided.  not eigenvectors)
