```julia
function spForm(P::Union{Mat, Real, Complex})
```

Measure of deviancy from scaled permutation form of $n⋅n$ square matrix `P`, defined as

$\frac{1}{2(n-1)}\bigg(\sum_{row}1-\beta(row)+\sum_{col}1-\beta(col)\bigg)$,

where for each *row* and *column* of `P`, β is the maximum of the absolute values divided by the sum of the absolute values.

This index is equal to $0$ if in each row and column $P$ has only one non-zero element, that is, if $P$ is a scaled permutation matrix. The larger the index, the farther away $P$ is from this form.

This measure and several existing variants are well-known in the blind source separation / independent component analysis community, where it is used to compare approximate joint diagonalization algorithms on simulated data. In fact, if $A$ is the inverse of the approximate joint diagonalizer that is used to generate the data and $B$ the approximate joint diagonalizer estimated by an algorithm, $P=BA$ must be as close as possible to a scaled permutation matrix (see [scale and permutation](@ref)).

Return 0.0 (zero) if `P` is a real of complex number.

**Examples:**

```julia
using Diagonalizations, PosDefManifold
# create 20 random commuting matrices
# they all have the same eigenvectors
Cset=randP(3, 20; eigvalsSNR=Inf, commuting=true)
# estimate the approximate joint diagonalizer (ajd)
a=ajd(Cset)
# the ajd must be equivalent to the eigenvector matrix of
# any of the matrices in Cset
spForm(a.F'*eigvecs(Cset[1]))+1.0≈1.0 ? println(" ⭐ ") : println(" ⛔ ")
```
