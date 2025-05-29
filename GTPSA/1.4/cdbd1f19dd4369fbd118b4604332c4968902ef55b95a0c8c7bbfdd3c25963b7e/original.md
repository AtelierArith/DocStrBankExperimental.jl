```
GTPSA.jacobiant(m::AbstractArray{<:TPS}; include_params=false) where {N,P,I}
```

Extracts the first-order partial derivatives (evaluated at 0) from the array of TPSs,  as the transpose of the Jacobian. The partial derivatives wrt the parameters will also  be extracted when the `include_params` flag is set to `true`. Note that this function is  not calculating anything - just extracting the first-order monomial coefficients already  in the TPSs.

### Input

  * `m`              – Array of TPSs to extract the Jacobian from, must be 1-based indexing
  * `include_params` – (Optional) Extract partial derivatives wrt parameters. Default is false

### Output

  * `Jt`             – Transpose of the Jacobian of `m`
