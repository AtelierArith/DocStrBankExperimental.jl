`sim_sir_gillespie(g::AbstractGraph, model::AbstractSIRModel, simdata::SIRSimData, rng::AbstractRNG, patient_zeros::Vector{<:Integer}; infect_IorS=:I, max_revive=0, debug=false, counts_func=count_SIR_states)`

最適化されたギレスピーアルゴリズムと優先度キューを使用してSIRシミュレーションを実行します。

### オプション引数

  * `infect_IorS`: 感染率が感染者（`:I`）または感受性（`:S`）ノードから来るかどうか。デフォルトは`:I`（`get_p_infection`を参照）。
  * `max_revive`: ノードが回復後に再感染できる最大回数。デフォルトは`0`。
  * `debug`: デバッグ情報の印刷を有効にします。デフォルトは`false`。
  * `counts_func`: 状態をカウントするカスタム関数。デフォルトは`count_SIR_states`。
