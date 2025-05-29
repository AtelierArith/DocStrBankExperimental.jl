hosvd1(X,Y; <keyword arguments>)

Hadamard product of ttensors X and Y as ttensor. Creates the product and calls hosvd. See also: hosvd2, hosvd3, hosvd4.

## Arguments:

  * `method` ∈ {"svd","lanczos","randsvd"}. Method for SVD. Default: "randsvd".
  * `reqrank::Vector`: Requested mutlilinear rank. Optional.
  * `eps_abs::Number/Vector`: Drop singular values (of mode-n matricization) below eps_abs. Optional.
  * `eps_rel::Number/Vector`: Drop singular values (of mode-n matricization) below eps*rel*sigma*1. Optional.
  * `p::Integer`: Oversampling parameter. Defaul p=10.
