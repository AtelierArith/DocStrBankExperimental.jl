`run_sir_fast(g::AbstractGraph, model::AbstractSIRModel, T::Integer, rng::AbstractRNG, patient_zeros::Vector{<:Integer}; beta_IorS=:I, dtype=Float64, counter=BaseSIRStatesCounter())`

高速SIRおよびSIR類似シミュレーションを設定して実行し、シミュレーションデータと状態カウントを返します。

`beta_IorS`引数は、デフォルトのSIRモデル(::SIRModel)でのみ使用されます。他のモデルには感染確率の計算のための独自の方法があります。

### オプション引数

  * `beta_IorS`: 感染ルール — 感染者(`:I`)、感受性者(`:S`)、または他の値の場合はその平均に基づくかどうか。デフォルトは`:I`。
  * `dtype=Float64`: 出力配列のデータ型。
  * `counter=BaseSIRStatesCounter()`: 状態カウント方法。
