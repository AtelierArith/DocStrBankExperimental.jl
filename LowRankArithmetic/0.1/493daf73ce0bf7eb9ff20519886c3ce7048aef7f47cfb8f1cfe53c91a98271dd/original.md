```
X = U*S*V'

SVD like factorization of a low rank matrix into factors U ∈ ℝⁿˣʳ, S ∈ ℝʳˣʳ, V ∈ ℝᵐˣʳ. 
The columns of U span the range of X, the colomuns of V span the co-range of X and S describes the map between
co-range and range. The factorization is non-unique and U and V need not be orthogonal! 
However, often U and V are chosen orthogonal to allow for cheap (pseudo)inversion. In that case, note that
orthogonality of U and V is not guaranteed to and in fact will rarely be preserved under the operations that
are supported (multiplication, addition, etc.). In order to reorthonormalize U and V, simply call `orthonormalize!(X, alg)`
where alg refers to the algorithm used to compute the orthonormalization: 
    * QRFact()
    * SVDFact()
    * GradientDescent()
```
