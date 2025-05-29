```
GTPSA.jacobian(m::AbstractArray{<:TPS}; include_params=false)
```

Extracts the first-order partial derivatives (evaluated at 0) from the array of TPSs.  The partial derivatives wrt the parameters will also be extracted when the `include_params`  flag is set to `true`. Note that this function is not calculating anything - just extracting  the first-order monomial coefficients already in the TPSs.

### Input

  * `m`              – Array of TPSs to extract the Jacobian from, must be 1-based indexing
  * `include_params` – (Optional) Extract partial derivatives wrt parameters. Default is false

### Output

  * `J`              – Jacobian of `m`
