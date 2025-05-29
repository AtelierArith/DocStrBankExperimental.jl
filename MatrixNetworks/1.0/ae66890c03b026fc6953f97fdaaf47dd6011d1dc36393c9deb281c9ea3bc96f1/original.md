## `fiedler_vector`

Compute the Fiedler vector associated with the normalized Laplacian of the graph with adjacency matrix A.

This function works with Float32 and Float64-valued sparse matrices and vectors.

It requires a symmetric input matrix representing the adjacency matrix of an undirected graph. If the input is a disconnected network then the result may not

The return vector is signed so that the number of positive entries is at least the number of negative entries. This will always give a unique, deterministic output in the case of a non-repeated second eigenvalue.

## Functions

  * `(v,lam2) = fiedler_vector(A::SparseMatrixCSC{V,Int})`
  * `(v,lam2) = fiedler_vector(A::MatrixNetwork{V,Int})`

## Inputs

  * `A`: the adjacency matrix
  * Optional Keywoard Inputs

      * `checksym`: ensure the matrix is symmetric
      * `tol`: the residual tolerance in the eigenvalue, eigenvector estimate. (This is an absolute error)
      * `maxiter`: the maximum iteration for ARPACK
      * `nev`: the number of eigenvectors estimated by ARPACK
      * `dense`: the threshold for a dense (LAPACK) computation instead of a sparse (ARPACK) computation. If the size of the matrix is less than `dense` then maxiter and nev are ignored and LAPACK computes all the eigenvalues.

## Returns

  * `v`: The Fiedler vector as an array
  * `lam2`: the eigenvalue itself

## Example

```
# construct an n-node path graph
n = 25
A = sparse(1:n-1,2:n,1.,n,n)
A = A + A'
(v,lam2) = fiedler_vector(A) # returns a cosine-like fiedler vector
# using UnicodePlots; lineplot(v)
```
