```
Random.rand!(
    rng::AbstractRNG,
    M::MultinomialSymmetricPositiveDefinite,
    p::AbstractMatrix,
)
```

Generate a random point on [`MultinomialSymmetricPositiveDefinite`](@ref) manifold. The steps are as follows:

1. Generate a random [totally positive matrix](https://en.wikipedia.org/wiki/Totally_positive_matrix)  a. Construct a vector `L` of `n` random positive increasing real numbers.  b. Construct the [Vandermonde matrix](https://en.wikipedia.org/wiki/Vandermonde_matrix)     `V` based on the sequence `L`.  c. Perform LU factorization of `V` in such way that both L and U components have     positive elements.  d. Convert the LU factorization into LDU factorization by taking the diagonal of U     and dividing U by it, `V=LDU`.  e. Construct a new matrix `R = UDL` which is totally positive.
2. Project the totally positive matrix `R` onto the manifold of [`MultinomialDoubleStochastic`](@ref) matrices.
3. Symmetrize the projected matrix and return the result.

This method roughly follows the procedure described in https://math.stackexchange.com/questions/2773460/how-to-generate-a-totally-positive-matrix-randomly-using-software-like-maple
