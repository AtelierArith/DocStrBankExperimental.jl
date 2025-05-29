`gillespie_sir_direct(g::AbstractGraph, model::AbstractSIRModel, simdata::SIRSimData, rng::AbstractRNG, patient_zeros::Vector{I}; ignore_infector=false, infect_IorS=:I) where I<:Integer`

直接サンプリングギレスピー法を使用してSIRシミュレーションを実行し、イベント処理を改善するためにバイナリツリーを使用します。これは推奨される方法ではなく、`sim_sir_gillespie`を使用することをお勧めします。

### オプション引数

  * `ignore_infector`: trueの場合、シミュレーションは各ノードを感染させた人を記録しません。デフォルトは`false`です。
  * `infect_IorS`: 感染が感染したノード（`:I`）または感受性ノード（`:S`）から始まるかどうか。デフォルトは`:I`です。
