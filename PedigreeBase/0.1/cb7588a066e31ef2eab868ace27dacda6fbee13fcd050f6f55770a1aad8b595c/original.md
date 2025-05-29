```
A = get_nrm(pedlist [, check=false, sorthere=true])
A = get_nrm(T, pedlist [, check=false, sorthere=true])
```

Calculates the numerator (or additive) relationship matrix, so-called *A-matrix* using the recursive ("tabular") method from the pedigree list `pedlist`. The pedigree must be sorted as the ancestors precede their progeny unless putting `sorthere=true`. The resulting matrix is dense. You can specify the type of `A` as `T` (Float64 by default). By default, this function checks if the pedigree is sorted chronologically or not; use `check=false` to turn it off. With the option `sorthere=true`, the function reorders the pedigree internally, and returns the correct A-matrix with the original order. However, it creates a temporary A-matrix with the reordered index, and it needs twice more memory.
