```
projection(M::AbstractMultispati)
```

Returns the projection matrix (of size `(d, p)`). Each column of the projection matrix corresponds to a eigenvector. The eigenvectors are arranged in ascending order of the eigenvalues.
