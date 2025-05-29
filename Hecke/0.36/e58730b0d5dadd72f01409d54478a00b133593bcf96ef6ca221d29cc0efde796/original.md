```
hnf(A::SMat{ZZRingElem}) -> SMat{ZZRingElem}
```

Return the upper right Hermite normal form of $A$.

$$
truncate
$$

indicates if zero rows should be returned or disgarded, when $full_hnf$ is set to $false$ only an upper triangular matrix is computed, ie. the upwards reduction is not performed.

$$
auto
$$

if set to true selects a different elemination strategy - here the upwards reduction is temporarily switched off.

$$
limit
$$

marks the last column where size reduction happens, so calling $hnf$ on $hcat(A, identity_matrix(SMat, ZZ, nrows(A)))$ with  $limit$ set to $ncols(A)$ should produce a non-reduced transformation matrix in the right. If $limit$ is not set, the transformation matrix will also be partly triangular.
