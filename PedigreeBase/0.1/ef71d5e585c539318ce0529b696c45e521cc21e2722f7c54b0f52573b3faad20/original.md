```
Ainv = get_nrminv(pedlist, f; rank=0)
Ainv = get_nrminv(pedlist; f, rank=0)
```

Computes the inverse of numerator (additive) relationship matrix using the "Henderson's" method from the pedigree list `pedlist` and inbreeding coefficients `f`. Without `f`, this function assumes zero inbreeding for all individuals. See Henderson (1976) and Quaas (1976) for details. The output is SparseMatrixCSC with the same type of elements with `f` while SparseMatrixDict (i.e., a hash matrix) is used as a temporary matrix. If you want to fix the size of A-inverse, specify `rank`. The function creates the inverse with either a bigger size: `rank` or the maximum ID in the pedigree.
