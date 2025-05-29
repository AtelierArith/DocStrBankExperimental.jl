```
hosvd(X; <keyword arguments>)
```

Higher-order singular value decomposition.

## Arguments:

  * `X`: Tensor (multidimensional array) or ttensor.
  * `method` ∈ {"svd","lanczos","randsvd"} Method for SVD. Default: "svd".
  * `reqrank::Vector`: Requested mutlilinear rank. Optional.
  * `eps_abs::Number/Vector`: Drop singular values (of mode-n matricization) below eps_abs. Default: 1e-8.
  * `eps_rel::Number/Vector`: Drop singular values (of mode-n matricization) below eps*rel*sigma*1. Optional.
  * `p::Integer`: Oversampling parameter. Defaul p=10.
