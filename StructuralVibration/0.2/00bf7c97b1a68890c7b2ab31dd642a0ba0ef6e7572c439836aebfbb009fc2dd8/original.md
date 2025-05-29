```
modal_matrices(ωn, ξn)
```

Computes the modal mass, stiffness, and damping matrices

**Inputs**

  * `ωn`: Vector of natural frequencies
  * `ξn`: Modal damping

**Outputs**

  * `Kn`: Generalized stiffness matrix
  * `Mn`: Generalized mass matrix (identity matrix, due to mass normalization)
  * `Cn`: Generalized damping matrix
