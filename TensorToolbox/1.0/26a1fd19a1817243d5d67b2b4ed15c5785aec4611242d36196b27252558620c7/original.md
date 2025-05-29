hosvd3(X,Y; <keyword arguments>)

Hadamard product of ttensors X and Y as ttensor. Structure exploiting, works with (X ∗ Y)ₙ(X ∗ Y)ₙᵀ matrices. See also: hosvd1, hosvd2, hosvd4.

## Arguments:

  * `method` ∈ {"lanczos","randsvd"} Structure exploiting method for SVD. Default: "lanczos".
  * `reqrank::Vector`: Requested mutlilinear rank. Optional.
  * `variant` ∈ {'A','B'} Variant of multiplication (X ∗ Y)ₙ(X ∗ Y)ₙᵀ. Default: 'B'.
  * `eps_abs::Number/Vector`: Drop singular values (of mode-n matricization) below eps_abs. Optional.
  * `eps_rel::Number/Vector`: Drop singular values (of mode-n matricization) below eps*rel*sigma*1. Optional.
  * `p::Integer`: Oversampling parameter. Defaul p=10.
