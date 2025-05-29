```
iterate_higham(
   Y::Union{Hermitian,Diagonal},
   Dykstra::Union{Hermitian,Diagonal},
   W_root::Union{Hermitian,Diagonal},
   W_inv::Union{Hermitian,Diagonal},
   W_inv_sqrt::Union{Hermitian,Diagonal},
)
```

Do one iterate mapping the input matrix to the S space (of psd matrices) and then to the U space (unit diagonal and all other entries below 1 in absolute value). Returns the updated matrix and the next iterate's Dykstra correction.

### Inputs

  * `Y` - The matrix you want to project to the iterate towards the space of valid correlation matrices.
  * `Dykstra` - The Dykstra correction matrix.
  * `W_root` - The root of `W`.
  * `W_inv` - The inverse of `W`.
  * `W_inv_sqrt` - The root of the inverse of `W`.

### Outputs

  * A `Hermitian`.
  * An updated Dykstra correction matrix.

### References

Higham, N. J. 2001. Algorithm 3.3
