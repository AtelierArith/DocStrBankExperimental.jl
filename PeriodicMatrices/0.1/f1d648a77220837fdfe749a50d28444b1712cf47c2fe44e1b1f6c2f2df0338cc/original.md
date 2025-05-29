```
psreduc_reg(A,E) -> (M, N)
```

Determine for a pair of `n×n×p` arrays `(A,E)`, the matrix pair `(M, N)`  with `M-λN` regular, such that  the eigenvalues of `M-λN` are the same as those of the quotient matrix product `inv(E(p))*(A(p)*inv(E(p-1))*A(p-1)*...*inv(E(1))*A(1)`, where `A(i)` is contained in `A[:,:,i]` and `E(i)` is contained in `E[:,:,i]`.  The structure exploiting fast reduction method of [1] is employed to determine `M` and `N`.

[1] A. Varga & P. Van Dooren. Computing the zeros of periodic descriptor systems.     Systems and Control Letters, 50:371-381, 2003.
