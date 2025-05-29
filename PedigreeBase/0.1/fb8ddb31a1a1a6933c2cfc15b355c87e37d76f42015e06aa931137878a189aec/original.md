```
Ainv = get_mgsnrminv(mgslist; rank=0)
```

Computes the inverse of numerator (additive) relationship matrix using the "Henderson's" method from the pedigree list `mgslist` with sire and maternal-grandsire (MGS). The inbreeding will be ignored. See Henderson (1975) for details. The output is SparseMatrixCSC with Float64 while SparseMatrixDict (i.e., a hash matrix) is used as a temporary matrix. If you want to fix the size of A-inverse, specify `rank`. The function creates the inverse with either a bigger size: `rank` or the maximum ID in the pedigree.
