```
colspace(X; <keyword arguments>)
```

Column space basis.

## Arguments:

  * `X`: Matrix.
  * `method` ∈ {"svd","lanczos","randsvd"} Method for SVD. Default: "svd".
  * `maxrank::Integer`: Maximal rank. Optional.
  * `atol::Number`: Drop singular values below atol.  Default: 1e-8.
  * `rtol::Number`: Drop singular values below rtol*sigma_1. Optional.
  * `p::Integer`: Oversampling parameter used by lanczos and randsvd methods. Defaul p=10.
