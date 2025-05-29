```
eigenmode(K, M, n = size(K, 1))
```

Computes the eigenmodes of a system defined by its mass and stiffness matrices.

**Inputs**

  * `K`: Stiffness matrix
  * `M`: Mass matrix
  * `n`: Number of modes to be keep in the modal basis

**Outputs**

  * `ω`: Vector of natural frequencies
  * `Φ`: Mass-normalized mode shapes
