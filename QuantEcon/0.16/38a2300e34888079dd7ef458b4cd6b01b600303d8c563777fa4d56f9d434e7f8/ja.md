与えられたポリシー `sigma` に対して、報酬ベクトル `R_sigma` と遷移確率行列 `Q_sigma` を返します。

##### パラメータ

  * `ddp::DiscreteDP` : モデルパラメータを含むオブジェクト
  * `sigma::AbstractVector{Int}`: ポリシールールベクトル

##### 戻り値

  * `R_sigma::Array{Float64}`: `sigma` の報酬ベクトル、長さ `n`。
  * `Q_sigma::Array{Float64}`: `sigma` の遷移確率行列、形状 `(n, n)`。
