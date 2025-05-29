```
VJP_λ_∂SIA∂H_continuous(
    λ::Matrix{R},
    H::Matrix{R},
    simulation::SIM,
    t::R;
    batch_id::Union{Nothing, I} = nothing
)
```

Hに関するSIA2D方程式の連続共役の実装。λとHが与えられると、λ^T * ∂(SIA2D)/∂H (H) のVJPを返します。

引数:

  * `λ::Matrix{R}`: 共役状態、逆モードADにおける出力勾配とも呼ばれます。
  * `H::Matrix{R}`: SIA2Dの入力状態に対応する氷の厚さ。
  * `simulation::SIM`: シミュレーションパラメータ。
  * `t::R`: 時間値、SIA2Dは時間に依存しないため使用されません。
  * `batch_id::Union{Nothing, I}`: バッチインデックス。

返り値:

  * `dλ::Matrix{R}`: ヤコビアンベクトル積、逆モードADにおける入力勾配とも呼ばれます。
