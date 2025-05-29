```
 pm2lpCF1(P; grade = l) -> (M, N)
```

Build a strong linearization `M - λN` of a polynomial matrix `P(λ)` in the first companion Frobenius form. 

`P(λ)` is a grade `k` polynomial matrix assumed of the form `P(λ) = P_1 + λ P_2 + ... + λ**k P_(k+1)`, with  the coefficient matrices `P_i`, `i = 1, ..., k+1` stored in the 3-dimensional matrix `P`,  where `P[:,:,i]` contains the `i`-th coefficient matrix `P_i` (multiplying `λ**(i-1)`).  The effective grade `l` to be used for linearization can be specified via the keyword argument `grade` as  `grade = l`, where `l` must be chosen equal to or greater than the degree of `P(λ)`. The default value used for `l` is `l = deg(P(λ))`.

`P(λ)` can also be specified as a matrix, vector or scalar of elements of the `Polynomial` type  provided by the [Polynomials](https://github.com/JuliaMath/Polynomials.jl) package.   

If `P(λ)` is a `m x n` polynomial matrix of effective grade `l` and degree `d`,  then the resulting matrix pencil `M - λN` satisfies the following conditions [1]:

(1) `M - λN` has dimension `(m+n*(l-1)) x n*l` and `M - λN` is regular if `P(λ)` is regular;

(2) `M - λN` and `P(λ)` have the same finite eigenvalues;

(3) the partial multiplicities of infinite eigenvalues of `M - λN` are in excess with `l-d` to the partial multiplicities of the infinite eigenvalues of `P(λ)`;

(4) `M - λN` and `P(λ)` have the same number of right Kronecker indices and the right Kronecker indices of `M - λN` are in excess with `l-1` to the right Kronecker indices of `P(λ)`;

(5) `M - λN` and `P(λ)` have the same left Kronecker structure (i.e., the same left Kronecker indices).

[1] F. De Terán, F. M. Dopico, D. S. Mackey, Spectral equivalence of polynomial matrices and the Index Sum Theorem, Linear Algebra and Its Applications, vol. 459, pp. 264-333, 2014.
