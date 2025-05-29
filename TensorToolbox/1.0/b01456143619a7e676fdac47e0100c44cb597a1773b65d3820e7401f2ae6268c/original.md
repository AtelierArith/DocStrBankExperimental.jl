krontm(X,Y,M[,modes,t='n'])

Kronecker product of two tensors times matrix (n-mode product): (X ⊗ Y) x₁ M₁ x₂ M₂ x₃ ⋯ xₙ Mₙ.

## Arguments:

  * `X::Array`
  * `Y::Array`
  * `M::Matrix/MatrixCell`
  * `modes::Integer/Vector` : Modes for multiplication. Default: 1:length(M).
  * `t='t'`: Transpose matrices from M.
