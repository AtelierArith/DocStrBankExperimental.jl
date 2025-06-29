```
svdsketch(A[, tol]; [maxrank, blocksize, maxiter, poweriter]) -> (U, S, V, apxerror)
```

Returns the singular value decomposition (SVD) of a low-rank matrix sketch of $A$. The matrix sketch only reflects the most important features of $A$ (up to a tolerance), which enables faster calculation of the SVD of large matrices compared to using `svds`.

The sketch of $A$ satisfies that $\|U \Sigma V^T - A\|_F / \|A\|_F \leq \text{tol}$. The default value for `tol` is `eps(eltype(A))^(1/4)`.

In addition to the SVD, the vector `apxerror` is returned, whose entries represent the relative approximation error in each iteration, $\|U \Sigma V^T - A\|_F / \|A\|_F$. The length of `apxerror` is equal to the number of iterations, and `apxerror[end]` is the relative approximation error of the output.

# Options

`maxrank`: The rank of the matrix sketch will not exceed `maxrank`. The default value is `minimum(size(A))`.

`blocksize`: A larger value reduces the number of needed iterations, but might also result in the result having higher rank than necessary to achieve convergence. The default value is `min(max(floor(Integer, 0.1*size(A, 1)), 5), maxrank)`.

`maxiter`: The maximum number of iterations for the algorithm. The default value is `maxrank ÷ blocksize`.

`poweriter`: The number of power iterations performed within each iteration of the algorithm. Power iterations improve the orthogonality of the $U$ and $V$ outputs. The default value is 1.
