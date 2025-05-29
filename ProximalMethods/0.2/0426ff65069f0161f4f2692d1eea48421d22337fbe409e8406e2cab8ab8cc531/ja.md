```
prox_grad(x0, f, ∇f!, prox!; style=:noaccel, β=.5, ϵ=1e-7, max_iter=1000)
```

目的関数 $f(x) + g(x)$ を最小化します。ここで、$f(x)$ は微分可能ですが、$g(x)$ はそうではありません。近接勾配法を使用します。

#### 引数

  * `x0::AbstractVector`    : 初期パラメータ値 (n x 1)
  * `f::Function`           : $f(x)$
  * `∇f!::Function`         : $f$ の勾配
  * `prox!::Function`       : $g(x)$ の近接演算子
  * `style::Symbol`         : 加速スタイル
  * `β::Real`               : ラインサーチパラメータ
  * `ϵ::Real`               : 許容誤差
  * `max_iter::Integer`     : 最大反復回数

#### 戻り値

  * `x::AbstractVector` : 最小化点 (最適パラメータ値) (n x 1)
