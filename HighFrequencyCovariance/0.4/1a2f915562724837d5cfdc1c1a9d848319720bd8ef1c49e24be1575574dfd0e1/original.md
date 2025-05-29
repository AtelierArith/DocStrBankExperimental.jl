```
project_to_U(A::Union{Diagonal,Hermitian}, invW::Hermitian)

project_to_U(A::Union{Diagonal,Hermitian}, invW::Diagonal)
```

This maps the Hermitian/Hermitian matrix `A` to the nearest matrix in the U space (the space of all unit diagonal matrices as defined by Higham 2001). The inverse weight matrix `invW` determines how much to adjust each element to get it to be unit diagonal. In other words it is used to determine what is the nearest correlation matrix. The weight matrix must be Hermitian positive definite. We use the W-norm (as defined by Higham 2001).

### Inputs

  * `A` - The matrix you want to project to the U space
  * `invW` - The inverse weighting matrix.

### Outputs

  * A `Diagonal` or a `Hermitian`.

### References

Higham, N. J. 2001. Bottom of page 335.
