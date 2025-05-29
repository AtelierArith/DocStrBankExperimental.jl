```
X = U*Z'

Two factor factorization of a low rank matrix into factors U ∈ ℝⁿˣʳ and Z ∈ ℝᵐˣʳ. 
U should span the range of X while Z spans the co-range. The factorization is non-unique and
U need not be orthogonal! However, U is often chosen orthogonal for cheap (pseudo)inversion. In that case,
note that orthogonality of U is not guaranteed to and in fact will rarely be preserved under the operations that
are supported (multiplication, addition, etc.). In order to reorthonormalize U, simply call `orthonormalize!(X, alg)`
where alg refers to the algorithm used to compute the orthonormalization: 
    * GradientDescent() 
    * QRFact()
    * SVDFact()
```
