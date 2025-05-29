```
VJP_λ_∂SIA_discrete(
    ∂dH::Matrix{R},
    H::Matrix{R},
    simulation::SIM,
    t::R;
    batch_id::Union{Nothing, I} = nothing
)
```

浅氷近似PDEのアウトオブプレイス随伴ステップを計算します。出力勾配を与えると、勾配が入力HとAに逆伝播されます。ある程度、この関数はVJP*λ*∂SIA∂H*continuousおよびVJP*λ*∂SIA∂θ*continuousと同等です。

引数:

  * `∂dH::Matrix{R}`: 逆伝播する出力勾配。
  * `H::Matrix{R}`: SIA2Dの入力状態に対応する氷の厚さ。
  * `simulation::SIM`: シミュレーションパラメータ。
  * `t::R`: 時間値、SIA2Dは時間に依存しないため使用されません。
  * `batch_id::Union{Nothing, I}`: バッチインデックス。

戻り値:

  * `∂H::Matrix{R}`: Hに関する入力勾配。
  * `∂A::F`: Aに関する入力勾配。
