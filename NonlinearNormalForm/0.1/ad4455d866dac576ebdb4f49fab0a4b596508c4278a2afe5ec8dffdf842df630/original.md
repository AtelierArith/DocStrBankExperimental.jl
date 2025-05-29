```
moveback_unstable!(F::Eigen) -> Int
```

Moves back eigenvectors with eigenvalues having a zero imaginary component to the end of  the `values` and `vectors` arrays in the Eigen struct, and returns the number of unstable  eigenvectors. 

Note that if more than 1 mode is unstable, the pair of eigenvectors corresponding to a mode  will not necessarily be next to each other at the end of the matrix.
