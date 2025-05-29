```
VJP_λ_∂SIA∂θ_continuous(
    θ,
    λ::Matrix{R},
    H::Matrix{R},
    simulation::SIM,
    t::R;
    batch_id::Union{Nothing, I} = nothing
)
```

θに関するSIA2D方程式の連続共役の実装。λ、H、およびθが与えられると、λ^T * ∂(SIA2D)/∂θ (θ) のVJPを返します。

引数:

  * `θ`: パラメータのベクトル
  * `λ::Matrix{R}`: 逆モードADにおける出力勾配とも呼ばれる共役状態。
  * `H::Matrix{R}`: SIA2Dの入力状態に対応する氷の厚さ。
  * `simulation::SIM`: シミュレーションパラメータ。
  * `t::R`: 時間値、SIA2Dは時間に依存しないため使用されません。
  * `batch_id::Union{Nothing, I}`: バッチインデックス。

返り値:

  * `dλ::Matrix{R}`: 逆モードADにおける入力勾配とも呼ばれるヤコビアンベクトル積。
