`ChebBasis(N)`: 

Chebyshev polynomials up to degree `N-1` (inclusive). i.e  basis with length `N`. The basis is ordered as 

$$
[1, x, 2x^2-1, 4x^3-3x, ..., 2xT_{N-1}(x)-T_{N-2}(x)]
$$

where `x` is input variable. 

The differences between `ChebBasis` and `chebyshev_basis` is that `ChebBasis`  computes the basis on the fly when it is compiled and it does not store the  recursion coefficients as in `chebyshev_basis`. There might be a small  performance benefit from this. 

Secondly, `ChebBasis` and `chebyshev_basis` use different normalization.
