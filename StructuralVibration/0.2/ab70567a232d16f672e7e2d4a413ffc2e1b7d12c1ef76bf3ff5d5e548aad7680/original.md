```
rayleigh_damping_matrix(K, M, α, β)
rayleigh_damping_matrix(K, M, ω1, ω2, ξ1, ξ2)
```

Compute the Rayleigh damping matrix for a given stiffness and mass matrices

**Inputs**

  * `K`: Stiffness matrix
  * `M`: Mass matrix
  * Construction parameters

      * Method 1

          * `α`: Mass proportional damping coefficient
          * `β`: Stiffness proportional damping coefficient
      * Method 2

          * `ω1`: First natural frequency
          * `ω2`: Second natural frequency
          * `ξ1`: Damping ratio for the first natural frequency
          * `ξ2`: Damping ratio for the second natural frequency

**Output**

  * `C`: Rayleigh damping matrix
