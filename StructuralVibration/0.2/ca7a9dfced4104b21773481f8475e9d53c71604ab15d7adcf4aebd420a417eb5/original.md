```
impulse_response(K::Matrix{Float64}, M::Matrix{Float64}, ξn, t, n = size(K, 1); ismat = false)
```

Compute the impulse response of a multi-degrees of freedom (Mdof) system using the modal approach

**Inputs**

  * `K`:

      * If `ismodal = false`: Stiffness matrix
      * If `ismodal = true`: Squared natural angular frequencies
  * `M`:

      * If `ismodal = false`: Mass matrix
      * If `ismodal = true`: Mass-normalized mode shapes
  * `ξn`: Damping ratios
  * `t`: Time points at which to evaluate the response
  * `n`: Number of modes to retain in the modal basis
  * `ismodal::Bool`: Flag to indicate if the problem contains modal data
  * `ismat::Bool`: Flag to indicate if the output should be a matrix

**Output**

  * `sol`: ModalImpulseSolution

      * `u`: Impulse response matrix
