hosvd4(X,Y; <keyword arguments>)

Hadamard product of ttensors X and Y as ttensor. Uses rank-1 randomized algorithm for finding range of (X ∗ Y)ₙ. If reqrank defined, calls additonal hosvd on updated core tensor. See also: hosvd1, hosvd2, hosvd3.

## Arguments:

  * `method` ∈ {"svd","lanczos","randsvd"} Method for SVD. Default: "svd".
  * `reqrank::Vector`: Requested mutlilinear rank. Optional.
  * `eps_abs::Number/Vector`: Drop singular values (of mode-n matricization) below eps_abs. Optional.
  * `eps_rel::Number/Vector`: Drop singular values (of mode-n matricization) below eps*rel*sigma*1. Optional.
  * `p::Integer`: Oversampling parameter. Defaul p=10.
