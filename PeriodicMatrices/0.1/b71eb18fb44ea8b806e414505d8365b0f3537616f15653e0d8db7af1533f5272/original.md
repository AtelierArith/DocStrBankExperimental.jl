```
psreduc_reg(A) -> (M, N)
```

Determine for a `n×n×p` array `A`, the matrix pair `(M, N)`  with `N` invertible and `M-λN` regular, such that  the eigenvalues of `M-λN` are the same as those of the matrix product `A(p)*A(p-1)*...*A(1)`, where `A(i)` is contained in `A[:,:,i]`.  The structure exploiting fast reduction method of [1] is employed to determine `M` and `N`.

[1] A. Varga & P. Van Dooren. Computing the zeros of periodic descriptor systems.     Systems and Control Letters, 50:371-381, 2003.
