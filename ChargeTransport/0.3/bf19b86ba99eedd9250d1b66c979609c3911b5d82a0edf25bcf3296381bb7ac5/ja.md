```julia
mutable struct ParamsNodal
```

物理的なノード、すなわち半導体デバイスのドリフト-拡散シミュレーションのための空間依存パラメータを保持する構造体です。

  * `dielectricConstant::Vector{Float64}`: ノード依存の誘電率。
  * `doping::Vector{Float64}`: 各ノードの対応するドーピング値を持つ1D配列。
  * `mobility::Matrix{Float64}`: 各ノードの各キャリア$\alpha$に対する対応する移動度値$\mu_\alpha$を持つ2D配列。
  * `densityOfStates::Matrix{Float64}`: 各ノードの各キャリア$\alpha$に対する対応する有効状態密度値$N_\alpha$を持つ2D配列。
  * `bandEdgeEnergy::Matrix{Float64}`: 各ノードの各キャリア$\alpha$に対する対応するバンドエッジエネルギー値$E_\alpha$を持つ2D配列。
