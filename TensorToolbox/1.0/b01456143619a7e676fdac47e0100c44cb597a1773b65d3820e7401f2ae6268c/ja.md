krontm(X,Y,M[,modes,t='n'])

二つのテンソルのクロネッカー積と行列の積 (n-モード積): (X ⊗ Y) x₁ M₁ x₂ M₂ x₃ ⋯ xₙ Mₙ.

## 引数:

  * `X::Array`
  * `Y::Array`
  * `M::Matrix/MatrixCell`
  * `modes::Integer/Vector` : 乗算のためのモード。デフォルト: 1:length(M).
  * `t='t'`: Mから行列を転置する。
