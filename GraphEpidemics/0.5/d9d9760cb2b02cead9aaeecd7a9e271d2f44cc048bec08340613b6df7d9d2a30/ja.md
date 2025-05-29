`sim_sir_fast(g::AbstractGraph, model::AbstractSIRModel, T::Integer, simdata::SIRSimData, rng::AbstractRNG, patient_zeros::Vector{I}; beta_IorS=:I, counter=BaseSIRStatesCounter()) where I<:Integer`

`T` タイムステップにわたる離散時間 SIR シミュレーションを実行し、データ構造はすでに設定されています。

### オプション引数

  * `beta_IorS=:I`: 感染確率を感染者 (`:I`)、感受性者 (`:S`)、またはその平均に基づけるかどうか。デフォルトは `:I` です。
  * `counter=BaseSIRStatesCounter()`: 状態カウント構造体。カスタム構造体を使用する場合は、`count_states(::BaseSIRStatesCounter, states::Vector)` を実装することを確認してください。
